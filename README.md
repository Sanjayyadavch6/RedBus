# RedBus
//Automate RedBus to book Tickets
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class RedbusAutomation {
  public static void main(String[] args) {
    // Set the path to the ChromeDriver executable
    System.setProperty("webdriver.chrome.driver", "D:\\Selenium Drivers\\Chrome Driver\\chromedriver.exe");

    // Create a new instance of the ChromeDriver
    WebDriver driver = new ChromeDriver();

    // Navigate to the Redbus website
    driver.get("https://www.redbus.in/");

    // Find the "From" field and enter "Bangalore"
    WebElement fromField = driver.findElement(By.id("src"));
    fromField.sendKeys("Bangalore");

    // Find the "To" field and enter "Hyderabad"
    WebElement toField = driver.findElement(By.id("dest"));
    toField.sendKeys("Hyderabad");

    // Find the "Search Buses" button and click it
    WebElement searchBusesButton = driver.findElement(By.id("search_btn"));
    searchBusesButton.click();

    // Wait for the search results to load
    WebDriverWait wait = new WebDriverWait(driver, 10);
    wait.until(ExpectedConditions.presenceOfElementLocated(By.xpath("//div[@id='seat-layout-overlay']")));

    // Verify that the search results page has loaded
    WebElement seatLayoutOverlay = driver.findElement(By.xpath("//div[@id='seat-layout-overlay']"));
    if (seatLayoutOverlay.isDisplayed()) {
      System.out.println("Search results page loaded successfully");
    } else {
      System.out.println("Search results page failed to load");
    }

    // Close the browser
    driver.quit();
  }
}
