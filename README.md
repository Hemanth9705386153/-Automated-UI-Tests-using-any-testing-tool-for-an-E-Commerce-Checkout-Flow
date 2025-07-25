# Automated-UI-Tests-using-any-testing-tool-for-an-E-Commerce-Checkout-Flow
TEST 5

package Automation;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;
import io.github.bonigarcia.wdm.WebDriverManager;

public class Main_Framework {

    public static void main(String[] args) throws InterruptedException {

        WebDriverManager.chromedriver().setup();

        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        // Step 1: Open the website
        driver.get("http://www.automationpractice.pl/index.php");

        // Step 2: Click on "Sign in"
        driver.findElement(By.className("login")).click();
        Thread.sleep(2000);

        // Step 3: Enter login details
        driver.findElement(By.id("email")).sendKeys("hemanthvanka1234@gmail.com");
        driver.findElement(By.id("passwd")).sendKeys("hello");
        driver.findElement(By.id("SubmitLogin")).click();
        Thread.sleep(3000);

        // Step 4: Click on "Women" tab
        driver.findElement(By.linkText("Women")).click();
        Thread.sleep(3000);

        // Step 5: Click on the product (open details page)
        WebElement product = driver.findElement(By.xpath("(//a[@class='product-name'])[1]"));
        product.click();
        Thread.sleep(2000);

        // Step 6: Select size "M"
        WebElement sizeDropdown = driver.findElement(By.id("group_1"));
        Select selectSize = new Select(sizeDropdown);
        selectSize.selectByVisibleText("M");
        Thread.sleep(1000);

        // Step 7: Add to cart
        driver.findElement(By.name("Submit")).click();
        Thread.sleep(3000);

        // Step 8: Click "Proceed to checkout" from modal
        driver.findElement(By.xpath("//a[@title='Proceed to checkout']")).click();
        Thread.sleep(3000);

        // Step 9: Summary - Proceed
        driver.findElement(By.xpath("//p[@class='cart_navigation clearfix']//a[@title='Proceed to checkout']")).click();
        Thread.sleep(2000);

        // Step 10: Address - Proceed
        driver.findElement(By.name("processAddress")).click();
        Thread.sleep(2000);

        // Step 11: Agree to terms and Proceed (Shipping)
        driver.findElement(By.id("cgv")).click();
        driver.findElement(By.name("processCarrier")).click();
        Thread.sleep(2000);

        // Step 12: Choose payment method (Bank wire)
        driver.findElement(By.className("bankwire")).click();
        Thread.sleep(2000);

        // Step 13: Confirm the order
        driver.findElement(By.xpath("//span[text()='I confirm my order']")).click();
        Thread.sleep(3000);

        System.out.println("✅ Order placed successfully!");

        // Step 14: Close browser
        driver.quit();
    }
}
