import requests
from typing import Optional, Dict

def fetch_product_name(article: str) -> Optional[str]:
    url = f"https://content-api.wildberries.ru/content/v2/object/charcs/{article}"


    headers = {
        "Authorization": "ВАШ API КЛЮЧ"
    }

    response = requests.get(url, headers=headers)
    if response.status_code == 200:
        return response.json()["data"]["subjectName"]
    else:
        return None

def fetch_product_price(article: str) -> Optional[str]:
    url = f"https://discounts-prices-api.wildberries.ru/api/v2/list/goods/filter/10?filterNmID={article}"

    headers = {
        "Authorization": "ВАШ API КЛЮЧ"
    }

    response = requests.get(url, headers=headers)
    if response.status_code == 200:
        return response.json()["data"]["ListGoods"]["Array"]["sizes"]["Array"]["price"]
    else:
        return None

def parse_product(product_name: str, product_size: str) -> Optional[Dict[str, str]]:

    return {
        "name": product_name,
        "price": product_size
    }


def get_wb_info(article: str) -> Optional[dict]:
    product_name = fetch_product_name(article)
    product_price = fetch_product_price(article)
    return parse_product(product_name, product_price)

product = get_wb_info("400682365")
