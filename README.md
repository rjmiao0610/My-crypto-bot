import requests

def get_eth_price():
    url = "https://api.bitopro.com/v3/tickers/eth_twd"
    response = requests.get(url)
    price = response.json()['data']['lastPrice']
    print("目前 BitoPro ETH 台幣價格是:", price)

get_eth_price()
