# sample
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;

import org.openqa.selenium.By;
import org.openqa.selenium.HasInputDevices;
import org.openqa.selenium.Keyboard;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
//import org.openqa.selenium.Selenium;

public class App 
{    
	public static  readwrite output;
	private static properties objprop=properties.getoutput();
	public  Properties objprops=new Properties();
	public static  String configPath;
 public static ChromeDriver driver;
	   
	public App(String configPath) throws IOException, NoSuchMethodException, RuntimeException {
		keyword keyword = new keyword();
		//method = keyword.getClass().getMethods();
		//capturescreenShot_method =Keywords.getClass().getMethod("captureScreenshot",String.class,String.class,String.class);			
		//objprops= new Properties();
		FileInputStream fs = new FileInputStream(configPath);
		objprops.load(fs);
		this.configPath=configPath;
	}

	    	  public static  void main(String[] args)throws Exception{
	    		try{

	    	    	 System.setProperty("webdriver.chrome.driver", "D:\\CRMTEST\\src\\main\\java\\chrome\\chromedriver.exe");

	    	    	 WebDriver  driver=new ChromeDriver();

  	

	    	driver.manage().window().maximize();

	    	driver.get(Constants.url);

	    		Thread.sleep(2000);


driver.findElement(By.xpath(objprop.getmsg("Email"))).sendKeys(objprop.getmsg("MailId"));

driver.findElement(By.xpath(objprop.getmsg("Password"))).sendKeys(objprop.getmsg("InPassword"));
driver.findElement(By.xpath(objprop.getmsg("Login"))).click();
Thread.sleep(1000);
driver.findElement(By.xpath(objprop.getmsg("CRM"))).click();
Thread.sleep(1000);
driver.findElement(By.id("HighlightCRMLead")).click();
	Thread.sleep(1000);

driver.findElement(By.xpath(objprop.getmsg("CreateLead"))).click();
Thread.sleep(1000);
readwrite Excel = new readwrite(Constants.outputpath);

for(int i=1;i<=4;i++){
	if(Excel.getCellData(Constants.AppSheet,1,2).equalsIgnoreCase("On")){
		System.out.println("Entered into if 1 ");
		Thread.sleep(1000);
	if(Excel.getCellData(Constants.CRMSheet,1,2).equalsIgnoreCase("On")){
		System.out.println("Entered into if 2 ");
		Thread.sleep(1000);
	if(Excel.getCellData(Constants.TestSheet1,1,3).equalsIgnoreCase("On")){
		System.out.println("Entered into if 3 ");
		Thread.sleep(1000);
	//driver.findElement(By.name(	Excel.getCellData(Constants.TestSheet1,1,4))).click();
	if(Excel.getCellData(Constants.TestSheet2,1,3).equalsIgnoreCase("On")){
		System.out.println("Entered into if 4 ");
		Thread.sleep(1000);
		//driver.findElement(By.name(	Excel.getCellData(Constants.TestSheet2,1,4))).click();

	
		
		//driver.findElement()


	

driver.findElement(By.xpath(objprop.getmsg("FirstName"))).sendKeys((Excel.getCellData(Constants.OutSheet, i,5)));

driver.findElement(By.xpath(objprop.getmsg("LastName"))).sendKeys((Excel.getCellData(Constants.OutSheet, i,6 )));

driver.findElement(By.xpath(objprop.getmsg("Title"))).sendKeys((Excel.getCellData(Constants.OutSheet, i,7 )));

driver.findElement(By.xpath(objprop.getmsg("LeadTypeIT"))).sendKeys((Excel.getCellData(Constants.OutSheet, i,8)));
//Select LeadType=new Select (driver.findElement(By.id("generalInfo_Leadtype")));
//LeadType.selectByVisibleText(Excel.getCellData(Constants.OutSheet, i,3));

//Select LeadStatus=new Select (driver.findElement(By.id("generalInfo_LeadStatus")));

//LeadStatus.selectByVisibleText(Excel.getCellData(Constants.OutSheet,i,4));

driver.findElement(By.xpath(objprop.getmsg("LeadStatusCreated"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,9)));

driver.findElement(By.xpath(objprop.getmsg("EmailField"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,10)));

String Q1="Contacted";

Thread.sleep(2000);
String Q2="Contact in Future";
if(Excel.getCellData(Constants.OutSheet,i,9)==Q1){

driver.findElement(By.xpath(objprop.getmsg("WayOfContactArrow"))).click();
WebElement WayOfContact=driver.findElement(By.xpath(objprop.getmsg("WayOfContact")));
WayOfContact.sendKeys((Excel.getCellData(Constants.OutSheet,i,28)));
WayOfContact.sendKeys(Keys.ENTER);

Thread.sleep(2000);
}
else if(Excel.getCellData(Constants.OutSheet,i,9)==Q2)
{



driver.findElement(By.xpath(objprop.getmsg("DateToContact"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,29)));	
}
Thread.sleep(2000);
driver.findElement(By.xpath(objprop.getmsg("LinkedinUrl"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,11)));
//String S=Excel.getCellData(Constants.OutSheet,i,7);

//int A = Integer.parseInt(S);
long A=Excel.getNumericCellValue(Constants.OutSheet,i,12);
String S=String.valueOf(A);

driver.findElement(By.xpath(objprop.getmsg("Phone"))).sendKeys(S);

long A0=Excel.getNumericCellValue(Constants.OutSheet,i,13);
String S0=String.valueOf(A0);

driver.findElement(By.xpath(objprop.getmsg("PrimaryMobile"))).sendKeys(S0);


long A1=Excel.getNumericCellValue(Constants.OutSheet,i,14);
String S1=String.valueOf(A1);

driver.findElement(By.xpath(objprop.getmsg("SecondaryMobile"))).sendKeys(S1);
long A2=Excel.getNumericCellValue(Constants.OutSheet,i,15);
String S2=String.valueOf(A2);

driver.findElement(By.xpath(objprop.getmsg("Fax"))).sendKeys(S2);

driver.findElement(By.xpath(objprop.getmsg("SecondaryEmail"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,16)));

driver.findElement(By.xpath(objprop.getmsg("CompanyName"))).sendKeys((Excel.getCellData(Constants.OutSheet,i,17)));
driver.findElement(By.xpath(objprop.getmsg("IndustryArrow"))).click();
WebElement In=driver.findElement(By.xpath(objprop.getmsg("Industry")));
In.sendKeys(Excel.getCellData(Constants.OutSheet,i,18));
In.sendKeys(Keys.ENTER);


driver.findElement(By.xpath(objprop.getmsg("GeoLocation"))).sendKeys(Excel.getCellData(Constants.OutSheet,i,19));
driver.findElement(By.xpath(objprop.getmsg("TimeZoneArrow"))).click();
WebElement TZ=driver.findElement(By.xpath(objprop.getmsg("TimeZone")));
TZ.sendKeys((Excel.getCellData(Constants.OutSheet,i,20)));
TZ.sendKeys(Keys.ENTER);


driver.findElement(By.xpath(objprop.getmsg("CountryArrow"))).click();
WebElement Country=driver.findElement(By.xpath(objprop.getmsg("Country")));
Country.sendKeys(Excel.getCellData(Constants.OutSheet,i,21));
Country.sendKeys(Keys.ENTER);
driver.findElement(By.xpath(objprop.getmsg("StateArrow"))).click();
WebElement State=driver.findElement(By.xpath(objprop.getmsg("State")));
State.sendKeys(Excel.getCellData(Constants.OutSheet,i,22));
State.sendKeys(Keys.ENTER);


driver.findElement(By.xpath(objprop.getmsg("Save"))).click();
Thread.sleep(1000);

//driver.findElement(By.xpath(objprop.getmsg("NextAction"))).sendKeys(Excel.getCellData(Constants.OutSheet,i,24));
//
//driver.findElement(By.xpath(objprop.getmsg("AssignedToArrow"))).click();
//WebElement AssignedTo=driver.findElement(By.xpath(objprop.getmsg("AssignedTo")));
//AssignedTo.sendKeys(Excel.getCellData(Constants.OutSheet,i,25));
//
//driver.findElement(By.xpath(objprop.getmsg("SelectDueDate"))).sendKeys(Excel.getCellData(Constants.OutSheet,i,26));
//
//driver.findElement(By.xpath(objprop.getmsg("CreateActionButton"))).click();


//driver.findElement(By.xpath(objprop.getmsg("ConvertToProspect"))).click();
//Thread.sleep(2000);
//if(driver.findElement(By.linkText("go to")).isDisplayed()){
//	
//	WebElement popup=driver.findElement(By.linkText("go to"));
//	popup.click();
//	Thread.sleep(2000);
	
//	Alert alert = driver.switchTo().alert();
//	driver.switchTo().alert();
//	//alert.accept();
//	alert.dismiss();
//WebElement Popup=(WebElement) driver.switchTo().frame(0);
	//popup.sendKeys(Keys.ENTER);
				//Actions action = new Actions(driver);
	// action.keyPressNative(Keys.ENTER.toString());
	  // action.sendKeys(Keys.ENTER).build().perform();
				//action.sendKeys(Keys.ENTER);
								   // Keyboard keyboard=( (HasInputDevices) driver).getKeyboard();
								   // keyboard.sendKeys(Keys.ENTER);
													//OpenQA.Selenium.Interactions.Actions action = new OpenQA.Selenium.Interactions.Actions(driver);
					//action.SendKeys(OpenQA.Selenium.Keys.Escape);

				   // Actions builder = new Actions(webDriverInstance);
				   // builder.sendKeys(Keys.RETURN).perform();

	//WebElement.sendKeys(Keys.RETURN);
	//driver.navigate().to("http://ifserp.azurewebsites.net/Dashboard/EditAccount?AccountId=6");
	//Actions action = new Actions(driver); action.sendKeys(Keys.RETURN);



	
//	driver.findElement(By.xpath(objprop.getmsg("NewOpportunity"))).click();
//
//	driver.findElement(By.xpath(objprop.getmsg("OppName"))).sendKeys(Excel.getCellData(Constants.OutSheet,i,30));
//	driver.findElement(By.xpath(objprop.getmsg("ContactNameArrow"))).click();
//	WebElement ContactName=	driver.findElement(By.xpath(objprop.getmsg("ContactName")));
//	ContactName.sendKeys(Excel.getCellData(Constants.OutSheet,i,31));
//	ContactName.sendKeys(Keys.ENTER);
//	driver.findElement(By.xpath(objprop.getmsg("OppSave"))).click();
//
//}
//else if(driver.findElement(By.xpath(objprop.getmsg("Convert"))).isDisplayed())
//{
//	driver.findElement(By.xpath(objprop.getmsg("Convert"))).click();
//
//	driver.findElement(By.xpath(objprop.getmsg("OppName"))).sendKeys(Excel.getCellData(Constants.OutSheet,i,30));
//
//	driver.findElement(By.xpath(objprop.getmsg("OppSave"))).click();
//}
//
readwrite Excel1 = new readwrite(Constants.outputpath);
for(int k=1;k<=6;k++){
Excel1.setCellData("CRM_Create_Lead_Steps","Pass",k,23);
}
driver.findElement(By.id("HighlightCRMLead")).click();
Thread.sleep(1000);

driver.findElement(By.xpath(objprop.getmsg("CreateLead"))).click();
Thread.sleep(1000);


	    		
	}
	else{
		System.out.println("Condition is not Satisfied");
	}
	}
	else{
		System.out.println("Condition is not Satisfied");
	}
	}
	else{
		System.out.println("Condition is not Satisfied");
	}
	}
	else{
		System.out.println("Condition is not Satisfied");
	}
	}
	
	
	

	    		
	    		}
	    	  
		    	 catch (InterruptedException e) {
		    		 
		    		e.printStackTrace();
	    		}
	    	  

	    	  }}


	



	    	  
