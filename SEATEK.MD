# Open WebUI - Seatek Setup Guide

## 1. Chuẩn bị

```bash
cd open-webui
sudo cp .env.example .env
```

## 2. Chạy lần đầu

```bash
sudo docker compose -f docker-compose.seatek.yaml up -d
```

## 3. Cập nhật / Restart

```bash
# Pull image mới nhất + restart
sudo docker compose -f docker-compose.seatek.yaml pull
sudo docker compose -f docker-compose.seatek.yaml up -d --force-recreate
```

## 4. Xem logs

```bash
sudo docker compose -f docker-compose.seatek.yaml logs -f open-webui
```

## 5. Tắt dự án

```bash
sudo docker compose -f docker-compose.seatek.yaml down
```

## 6. Truy cập

- **Open WebUI**: http://<server-ip>:3000

## 7. Tối ưu Ollama Server (172.16.105.167)

SSH vào server Ollama và chỉnh service:

```bash
sudo systemctl edit ollama.service
```

Thêm:

```ini
[Service]
Environment="OLLAMA_FLASH_ATTENTION=1"
Environment="OLLAMA_KV_CACHE_TYPE=q8_0"
Environment="OLLAMA_KEEP_ALIVE=-1"
Environment="OLLAMA_NUM_PARALLEL=4"
```

Restart:

```bash
sudo systemctl daemon-reload
sudo systemctl restart ollama
```