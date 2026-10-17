
L'archuitecture est assez simple
- 1 Central Server le Ui est ici https://localhost:4000/
- 1 CA de test avec OCSP et horodatage (TSA)
- 3 Security Servers (un serveur de gestion, un fournisseur, un consommateur) les ports 1000, 2000 et 3000
- Un service REST exposé et appelé entre les deux membres
Le truc c'est de configurer le cs, ensuite la partie la plus chiante c'est de connecter les ss au cs avec les certifcats, tsa bref  c'est un peu galere (possible de les signer ici http://localhost:8888/testca/ ) 
bref courage gng
```yml
x-ss: &ss
  image: niis/xroad-security-server-sidecar:7.7.0
  environment:
    XROAD_TOKEN_PIN: 123456xrd!
    XROAD_ADMIN_USER: xrd
    XROAD_ADMIN_PASSWORD: secret
    XROAD_LOG_LEVEL: INFO
  networks:
    - xroad-network
  depends_on:
    - cs
    - ca

services:
  cs:
    image: niis/xroad-central-server:noble-7.7.0
    container_name: cs
    environment:
      XROAD_TOKEN_PIN: 123456xrd!
    ports:
      - 4000:4000
    volumes:
      - cs-db:/var/lib/postgresql/16/main
      - cs-conf:/etc/xroad
    networks:
      - xroad-network

  ca:
    image: ghcr.io/nordic-institute/xrddev-testca:latest
    container_name: ca
    ports:
      - 8888:8888
    volumes:
      - ca-data:/home/ca
    networks:
      - xroad-network

  ss1:
    <<: *ss
    container_name: ss1
    ports: ["1000:4000", "1080:8080", "1443:8443"]
    volumes:
      - ss1-db:/var/lib/postgresql/16/main
      - ss1-conf:/etc/xroad
      - ss1-archive:/var/lib/xroad

  ss2:
    <<: *ss
    container_name: ss2
    ports: ["2000:4000", "2080:8080", "2443:8443"]
    volumes:
      - ss2-db:/var/lib/postgresql/16/main
      - ss2-conf:/etc/xroad
      - ss2-archive:/var/lib/xroad

  ss3:
    <<: *ss
    container_name: ss3
    ports: ["3000:4000", "3080:8080", "3443:8443"]
    volumes:
      - ss3-db:/var/lib/postgresql/16/main
      - ss3-conf:/etc/xroad
      - ss3-archive:/var/lib/xroad


  api:
    image: mccutchen/go-httpbin
    container_name: api
    networks:
      - xroad-network

volumes:
  cs-db:
  cs-conf:
  ca-data:
  ss1-db:
  ss1-conf:
  ss1-archive:
  ss2-db:
  ss2-conf:
  ss2-archive:
  ss3-db:
  ss3-conf:
  ss3-archive:

networks:
  xroad-network:
    name: xroad-network
    driver: bridge
```