import requests
import time

def get_eth_price():
    url = "https://api.bitopro.com/v3/tickers/eth_twd"
    try:
        response = requests.get(url)
        price = response.json()['data']['lastPrice']
        return float(price)
    except:
        return None

target_price = 62000.0 

print("--- 2026 自動化監控啟動 ---")

while True:
    current_price = get_eth_price()
    if current_price:
        if current_price > target_price:
            status = "🟢 價格尚高"
        else:
            status = "🔴 達到買點！"
        print(f"目前 ETH: {current_price} | 目標: {target_price} | 狀態: {status}")
    
    time.sleep(10)
