"# Small-Mart

A full-stack MERN e-commerce application with Braintree payment integration.

## Docker Hub

**Image:** [aashish2201/small-mart](https://hub.docker.com/r/aashish2201/small-mart)

## Quick Start

### Pull and Run from Docker Hub

```bash
docker pull aashish2201/small-mart:latest
```

```bash
docker run -d -p 8080:8080 \
  -e MONGO_URL=your_mongodb_connection_string \
  -e JWT_SECRET=your_jwt_secret \
  -e BRAINTREE_MERCHANT_ID=your_merchant_id \
  -e BRAINTREE_PUBLIC_KEY=your_public_key \
  -e BRAINTREE_PRIVATE_KEY=your_private_key \
  --name small-mart \
  aashish2201/small-mart:latest
```

Access the application at: **http://localhost:8080**

### Using Environment File

Create a `.env` file:

```env
PORT=8080
MONGO_URL=mongodb+srv://username:password@cluster.mongodb.net/ecommerce
JWT_SECRET=your_jwt_secret_key
BRAINTREE_MERCHANT_ID=your_merchant_id
BRAINTREE_PUBLIC_KEY=your_public_key
BRAINTREE_PRIVATE_KEY=your_private_key
```

Run with env file:

```bash
docker run -d -p 8080:8080 --env-file .env --name small-mart aashish2201/small-mart:latest
```

### Using Docker Compose

```yaml
version: '3.8'
services:
  app:
    image: aashish2201/small-mart:latest
    ports:
      - "8080:8080"
    environment:
      - MONGO_URL=${MONGO_URL}
      - JWT_SECRET=${JWT_SECRET}
      - BRAINTREE_MERCHANT_ID=${BRAINTREE_MERCHANT_ID}
      - BRAINTREE_PUBLIC_KEY=${BRAINTREE_PUBLIC_KEY}
      - BRAINTREE_PRIVATE_KEY=${BRAINTREE_PRIVATE_KEY}
    restart: unless-stopped
```

```bash
docker-compose up -d
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `MONGO_URL` | MongoDB connection string | Yes |
| `JWT_SECRET` | Secret key for JWT tokens | Yes |
| `BRAINTREE_MERCHANT_ID` | Braintree merchant ID | Yes |
| `BRAINTREE_PUBLIC_KEY` | Braintree public key | Yes |
| `BRAINTREE_PRIVATE_KEY` | Braintree private key | Yes |
| `PORT` | Server port (default: 8080) | No |

## Container Management

```bash
# View logs
docker logs small-mart

# Stop container
docker stop small-mart

# Start container
docker start small-mart

# Remove container
docker rm small-mart
```

## Build from Source

```bash
git clone https://github.com/your-username/small-mart.git
cd small-mart
docker build -t aashish2201/small-mart:latest .
docker run -d -p 8080:8080 --env-file .env --name small-mart aashish2201/small-mart:latest
```

## Tech Stack

- **Frontend:** React.js, Ant Design
- **Backend:** Node.js, Express.js
- **Database:** MongoDB
- **Payments:** Braintree
- **Container:** Docker
" 
