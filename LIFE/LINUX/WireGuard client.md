wg genkey | tee /etc/wireguard/goloburdin_privatekey | wg pubkey | tee /etc/wireguard/goloburdin_publickey


wg genkey | tee /etc/wireguard/pupa_privatekey | wg pubkey | tee /etc/pupa_publickey

[Interface]
PrivateKey = SN3ddOAIFadCu2NFKMqSf9CDrlr26je9w7aq7vgHOmI=
Address = 10.0.0.5/32
DNS = 8.8.8.8

[Peer]
PublicKey = DLxnk/uZl27UcoYOKim//Gy3TokeG5iz9UKuFXMOyjA=
Endpoint = 195.133.62.47:51830
AllowedIPs = 0.0.0.0/0
PersistentKeepalive = 20