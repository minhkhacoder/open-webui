
# Copy env

`cd open-webui`
`sudo cp .env.example .env`

# Run on Linux Server

`sudo docker compose -f docker-compose.seatek.yaml up -d --build`

# Run on Linux Server with GPU

`sudo docker compose -f docker-compose.seatek.yaml -f docker-compose.gpu.yaml up -d --build`