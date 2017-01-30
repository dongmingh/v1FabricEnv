##Create a fabric environment network or add peers to an existing network.


#Usage

    ./driver.sh [ceare|add] [nPeer] [nOrderer] [nBroker] [db]

- create or add
 - create: to create a new network with specified attributes
 - add: to add nPeer to the existing network, the nOrderer, nBroker, and db have to be the same as those when the network was created.
- nPeer: number of peers to be created or added
- nOrderer: number of orderers to be created
- nBroker: number of kafka brokers to be created, if 0, then solo is applied
- db:
 - couch: CouchDB
 - level: golevelDB

Note that 1 cop is created as default.
 
#IP addresses

The IP addresses and ports for peers and orderers needs to be included in the network.json, see network.json for detail.


#Examples

###With golevelDB: 

####example 1: create one cop, 4 peers, 3 orderer, 3 kafka brokers with golevelDB

    ./driver.sh create 4 3 3 level

####example 2: create one cop, 4 peers, 1 orderer, solo with golevelDB

    ./driver.sh create 4 1 0 level


####example 3: add 2 peers to the existing network which has 3 orderers, 3 kafka brokers with golevelDB

    ./driver.sh add 2 3 3 level



###with CouchDB:

####example 4: create 1 cop, 4 peers, 3 orderers, 3 kafka brokers with CouchDB

    ./driver.sh create 4 3 3 couch

####example 5: add 2 peers to the existing network which has 3 orderers and 3 kafka brokers with CouchDB

    ./driver.sh add 2 3 3 couch