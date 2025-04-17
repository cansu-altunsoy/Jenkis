package runners;

import io.cucumber.junit.Cucumber;
import io.cucumber.junit.CucumberOptions;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import org.junit.BeforeClass;
import org.junit.runner.RunWith;

@RunWith(Cucumber.class)
@CucumberOptions(
		features = "src/test/resources/features", // feature dosyalarının doğru yolu
		glue = "stepDefinitions",                 // step definitions'ın doğru yolu
		plugin = {
				"pretty",                          // Konsolda okunabilir loglar
				"html:target/cucumber-reports/cucumber.html", // HTML raporu
				"json:target/cucumber-reports/cucumber.json", // JSON raporu
				"io.qameta.allure.cucumber7jvm.AllureCucumber7Jvm" // Allure raporları
		},
		monochrome = true,                         // Konsol çıktısını daha okunabilir hale getirir
		tags = "@test03"                            // Yalnızca test03 etiketi olan senaryoları çalıştırır
)
public class TestRunner {
	private static final Logger logger = LogManager.getLogger(TestRunner.class);

	@BeforeClass
	public static void setup() {
		// Test çalışmaya başlamadan önce loglama yapılır
		logger.info("Cucumber Test Runner başlatılıyor...");
	}
}
