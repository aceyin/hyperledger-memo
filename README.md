# hyperledger memo

# Hyperledger网络初始化顺序
 - Generate certificates using cryptogen tool
   需要使用以下配置文件 crypto-config.yaml
   ```yaml
   OrdererOrgs:
   #---------------------------------------------------------
   # Orderer
   # --------------------------------------------------------
   - Name: Orderer
     Domain: example.com
   # ------------------------------------------------------
   # "Specs" - See PeerOrgs below for complete description
   # -----------------------------------------------------
    Specs:
      - Hostname: orderer
   # -------------------------------------------------------
   # "PeerOrgs" - Definition of organizations managing peer nodes
   # ------------------------------------------------------
   PeerOrgs:
   - Name: Org1
     Domain: org1.example.com
   ```
   
   输出产物保存在 crypto-config 文件夹，包以下内容：
   
```
    crypto-config
     |- ordererOrgnanizations
     |--- example.com (目录名称来源于 crypto-config.yaml > OrdererOrgs > Domain 的值)
     |----- ca (貌似没啥用)
     |----- msp (貌似没啥用)
     |----- orderers
     |-------- orderer.example.com
     |----------- msp (orderer节点的MSP身份认证文件)
     |------------- admincerts (管理员身份认证文件)
     |------------- cacerts ()
     |------------- keystore ()
     |------------- signcerts ()
     |------------- tlscacerts ()
     |----------- tls
     |-------------- ca.crt
     |-------------- server.crt
     |-------------- server.key
     |- peerOrganizations
     |--- org1.example.com
     |----- ca (貌似没啥用)
     |----- msp (貌似没啥用)
     |----- peers 
     |-------- peer0.org1.example.com
     |---------- msp
     |------------- admincerts (管理员身份认证文件)
     |------------- cacerts ()
     |------------- keystore ()
     |------------- signcerts ()
     |------------- tlscacerts ()
     |---------- tls
     |-------------- ca.crt
     |-------------- server.crt
     |-------------- server.key
     |-------- peer1.org1.example.com(结构与peer0.org1.example.com相同)
     |----- tlsca
     |----- users
     |--- org2.example.com(结构与org1.example.com相同)
 ```
 
 - Generating Orderer Genesis block  using configtxgen
 - Generating channel configuration transaction 'channel.tx'
 - Generating anchor peer update for origanizations
 
