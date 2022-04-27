import json
import requests
import pandas as pd

base_url="https://api.sportradar.us/soccer/trial/v4/en/seasons/sr:season:66441/standings.jsonapi_key=apikey"

response = requests.get(base_url)

sportsData = response.json()

df = pd.json_normalize(sportsData['standings'][0]['groups'][0]['standings'][0:])

df.to_csv('sportsData.csv', index = False)
