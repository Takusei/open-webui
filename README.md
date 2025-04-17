## Open WebUI to test ollama in local WSL
To make this app can connect ot ollama, have to change the setting in ollama to make them under same network
```
sudo nano /etc/systemd/system/ollama.service 

# Change to this:
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/local/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="OLLAMA_HOST=0.0.0.0:11434"
Environment="OLLAMA_ORIGINS=*"

[Install]
WantedBy=default.target
```
## Run this app
```
docker compose up -d
```

Refer:
https://github.com/ollama/ollama/issues/1431#issuecomment-2463691029
