# We are ServUT

Our purpose is to create a space where organizations can come together and provide solutions to uncommon needs.

## The Issue
### Non-profits are in need of human capital and student organizations can't easily find volunteering opportunities

Student organizations have to go through many layers of effort to find relevant ways to significantly impact their communities. Because of this friction, student groups prefer to volunteer with existing partnerships instead of searching for those with the most unmet need. Nonprofits also aren't able to easily indicate what resources they require (time, monetary, functional support, etc.)

## Our Solution
### Create a dynamic service marketplace where student organizations and nonprofit organizations can connect

This platform acts as a marketplace between student organizations and community services. Volunteer organizations can directly advertise their specific needs so student organizations can most efficiently deploy their resources. This allows student groups to help the nonprofits that have the most unmet need. Student organizations can also post on what causes they are most passionate about, allowing compatible nonprofits to find passionate support.

## Our Progress
### Finding a Need, Initial Concept, and Overcoming Technical Challenges
With so many potential ways to help, how could our team best help the community as novices in technology? After talking with the Texas Ramp Project, we discovered that there was a large unmet need for the mobility-impaired community in Travis County. This backlog could easily be solved if more student organizations knew about the Texas Ramp Project. 

We then realized that if Texas Ramp Project had this need, other nonprofit organizations likely do too. By creating a social marketplace where nonprofits could post their service needs for student organizations to fill, the needs of these underserved communities could be met more efficiently. Moreover, student organizations interested in certain causes or types of volunteering efforts (e.g. fundraising, construction, etc) could be contacted easily by the nonprofits that are relevant to those causes.

Our MVP was to aggregate student organization data into one easy-to-access page so nonprofits could easily contact them. By using the Selenium package in Python, we worked on webscraping the names and contact information of all student organizations at UT Austin through the [Hornslink](https://utexas.campuslabs.com/engage/) database.


## SourceCode
```code

from selenium import webdriver
from selenium.webdriver.common.keys import Keys



driver = webdriver.Chrome()
baseurl = "https://utexas.campuslabs.com/engage/organizations"
driver.get(baseurl)
elems = driver.find_elements_by_xpath("//*[@href]")
for elem in elems:

   if "https://utexas.campuslabs.com/engage/organization" in elem.get_attribute("href"):
      print()
      driver2 = webdriver.Chrome()
      driver2.get(elem.get_attribute("href"))

      name = driver2.find_element_by_tag_name('h1')
      name_content = name.get_attribute('text')
      print (name_content)
      driver2.quit()

driver.quit()

```

