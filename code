from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

import time

ClientProductFind=input("Enter product name: ")

service=Service()
option=webdriver.ChromeOptions()
driver=webdriver.Chrome(service=service,options=option)

class Product:
    def __init__(self, shop, name, price, link):
        self.shop = shop
        self.name = name
        self.price = price
        self.link = link

    def __str__(self):
        return f"{self.shop}\n{self.name}\n{self.price}\n{self.link}\n"

#LEMONA
url1="https://www.lemona.lv/"
driver.get(url1)

WebDriverWait(driver, 10).until(
    EC.presence_of_all_elements_located((By.CLASS_NAME, "ch2-allow-all-btn"))                               
)

find=driver.find_element(By.CLASS_NAME, "ch2-allow-all-btn")
find.click()

find=driver.find_element(By.NAME, "searchText")
find.send_keys(ClientProductFind)

find=driver.find_element(By.CLASS_NAME, "SearchBar-searchButton-1u0")
find.click()
time.sleep(1)

select_element = driver.find_element(By.NAME, "orderby")
select_element.click()

option_80 = driver.find_element(By.CSS_SELECTOR, 'select[name="orderby"] option[value="80"]')
option_80.click()

time.sleep(3)

WebDriverWait(driver, 20).until(
    EC.presence_of_all_elements_located((By.CSS_SELECTOR, "[class^='PriceBox-finalPrice-344']"))
)

product_list=[]

product_cards = driver.find_elements(By.CSS_SELECTOR, "[class^='ProductCard-productCard']")
for card in product_cards:
    shop = "LEMONA"
    try:
        name = card.find_element(By.CSS_SELECTOR, "[class^='ProductCard-productTitle-3oW']").text
    except:
        continue
    try:
        price = card.find_element(By.CSS_SELECTOR, "[class^='PriceBox-finalPrice-344']").text
    except:
        continue
    try:
        link = card.find_element (By.CSS_SELECTOR, "[class^='ProductCard-anchor-fC0']").get_attribute("href")
    except:
        continue
    product_list.append(Product(shop, name, price, link))

#ALIEXPRESS
url2 = "https://www.aliexpress.com/"
driver.get(url2)

WebDriverWait(driver, 10).until(
    EC.presence_of_all_elements_located((By.CLASS_NAME, "search--keyword--15P08Ji"))
)

searchBar = driver.find_element(By.CLASS_NAME, "search--keyword--15P08Ji")
searchBar.click()
searchBar.send_keys(ClientProductFind)

searchBtn = driver.find_element(By.CLASS_NAME, "search--newSubmit--3BlVRKw")
searchBtn.click()
time.sleep(5)

scroll_pause_time = 1
scroll_increment = 300
current_position = 0
document_height = driver.execute_script("return document.body.scrollHeight;")
while current_position < document_height:
    driver.execute_script("window.scrollBy(0, arguments[0]);", scroll_increment)
    time.sleep(scroll_pause_time)
    current_position += scroll_increment
    document_height = driver.execute_script("return document.body.scrollHeight;")

product_cards1 = driver.find_elements(By.CSS_SELECTOR, ".jr_g.h5_ia.search-card-item")

for card in product_cards1:
    shop = "ALIEXPRESS"
    try:
        name = card.find_element(By.CLASS_NAME, "jr_ae").get_attribute("title")
    except Exception:
        continue
    try:
        price = card.find_element(By.XPATH, ".//div[contains(@class, 'jr_kr')]").text.replace("\n", "").strip()
    except Exception:
        continue
    try:
        if card.tag_name.lower() == "a":
            link = card.get_attribute("href")
        else:
            link = card.find_element(By.TAG_NAME, "a").get_attribute("href")
    except Exception:
        continue
    product_list.append(Product(shop, name, price, link))

driver.quit()

#Quick sort
def parse_price(price_str):
    try: 
        price= float(price_str.replace("€", "").replace("$", "").replace(",", ".").strip())
        return price
    except:
        return float('inf')

    
def quick_sort(product):
    if len(product) <= 1:
        return product
    else:
        pivot = product[0]
        less_than_pivot = [x for x in product[1:] if parse_price(x.price) < parse_price(pivot.price)]
        greater_than_pivot = [x for x in product[1:] if parse_price(x.price) >= parse_price(pivot.price)]
        return quick_sort(greater_than_pivot) + [pivot] + quick_sort(less_than_pivot)
    
sorted_products = quick_sort(product_list)

# Print the sorted products
while(True) : 
    storeSort=input("Enter store: ")
    if storeSort == "EXIT":
        break 
    else:
        for product in sorted_products:
            if storeSort == "ALL":
                print(product)
                print("---------------------------------------------------------------------")
            elif storeSort.upper() in product.shop.upper():
                print(product)
                print("---------------------------------------------------------------------")
            else:
                continue
