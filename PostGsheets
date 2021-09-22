def GetOauth():
    url = "https://accounts.google.com/o/oauth2/token"
    payload = json.dumps({  "client_id": "your cliente id",
                            "client_secret": "your client secret",
                            "grant_type": "refresh_token",
                            "refresh_token": "your refresh_token"   })
    headers = {'Content-Type': 'text/plain'}
    response = requests.request("POST", url, headers=headers, data=payload)
    oauth = response.json()
    return oauth['access_token']

def POST(values):
    sheetid = "your sheet id"
    sheet_name = "your sheet name" 
    
    url = f"https://sheets.googleapis.com/v4/spreadsheets/{sheetid}/values/{sheet_name}!A1:append?insertDataOption=INSERT_ROWS&responseDateTimeRenderOption=FORMATTED_STRING&valueInputOption=USER_ENTERED"
    
    lines = str(values)
    payload = '{"values":'+lines+'}'
    headers = {'Authorization': "Bearer "+GetOauth()}          
    response = requests.post(url, headers = headers, data = payload)
    print(response.text)
    assert response.status_code == 200
