swagger: "2.0"
x-collection-name: Lisk
x-complete: 1
info:
  title: Lisk API Documentation
  description: -welcome-access-restrictionsthe-api-endpoints-are-by-default-restricted-to-a-whitelist-of-ips-that-can-be-found-in-config-json-in-the-section-api-access-whitelisthttpsgithub-comliskhqliskblob1-0-0config-jsonl35-if-you-want-your-api-to-be-accessable-by-the-public-you-can-do-this-by-changing-api-access-public-to-true-this-will-allow-anyone-to-make-requests-to-your-lisk-core-node-however-some-endpoints-stay-private-that-means-only-a-list-of-whitelisted-ips-can-successfully-make-api-calls-to-that-particular-endpointthis-includes-all-forging-related-api-calls-by-default-only-the-nodes-local-ip-is-included-in-the-whitelist-you-can-change-the-setting-in-config-json-in-the-section-forging-access-whitelisthttpsgithub-comliskhqliskblob1-0-0config-jsonl114-for-more-details-see-the-descriptions-at-the-respective-endpoint--requestschained-filter-parameters-are-logically-connected-with-and-http-is-the-supported-url-schema-by-default-to-enable-https-please-adjust-the-the-sslhttpsgithub-comliskhqliskblob1-0-0config-jsonl124-section-in-config-json--responsesthe-general-response-format-is-json-applicationjson-the-responses-for-each-api-request-have-a-common-basic-structurejavascriptdata--contains-the-requested-datameta--contains-additional-metadata-e-g--the-values-of-limit-and-offsetlinks--will-contain-links-to-connected-api-calls-from-here-e-g--pagination-links-date-formatsmost-of-the-timestamp-parameters-are-in-the-lisk-timestamp-format-which-is-similar-to-the-unix-timestamp-format-the-lisk-timestamp-is-the-number-of-seconds-that-have-elapsed-since-the-lisk-epoch-time-20160524t170000-000z-not-counting-leap-seconds-the-lisk-epoch-time-is-returned-in-the-iso8601httpsen-wikipedia-orgwikiiso-8601-format-combined-date-and-time-yyyymmddthhmmssz-for-details-see-the-descriptions-and-examples-at-the-respective-endpoint--paginationone-can-paginate-nicely-through-the-results-by-providing-limit-and-offset-parameters-to-the-requests-limit-and-offset-can-be-found-in-the-metaobject-of-the-response-of-an-api-request-if-no-limit-and-offset-are-provided-they-are-set-to-10-and-0-by-default-what-will-display-the-first-10-results--list-of-endpointsall-possible-api-endpoints-for-lisk-core-are-listed-below-click-on-an-endpoint-to-show-descriptions-details-and-examples-
  version: 1.0.0
basePath: /api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /spec:
    x-swagger-pipe:
      summary: ""
      description: ""
      operationId: ""
      x-api-path-slug: spec-xswaggerpipe
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - ""
  /transactions:
    post:
      summary: Submits signed transaction for processing
      description: |-
        Submits signed transaction object for processing by the transaction pool.
        Transaction objects can be generated locally either by using Lisk Commander or with Lisk Elements.
      operationId: postTransaction
      x-api-path-slug: transactions-post
      parameters:
      - in: body
        name: transaction
        description: Transaction object to submit to the network
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Submits
      - Signed
      - Transactionprocessing
    get:
      summary: Requests transactions data
      description: Search for a specified transaction in the system.
      operationId: getTransactions
      x-api-path-slug: transactions-get
      parameters:
      - in: query
        name: blockId
        description: Block id to query
      - in: query
        name: fromTimestamp
        description: Starting unix timestamp
      - in: query
        name: height
        description: Current height of the network
      - in: query
        name: id
        description: Transaction id to query
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: maxAmount
        description: Maximum transaction amount in Beddows
      - in: query
        name: minAmount
        description: Minimum transaction amount in Beddows
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: recipientId
        description: Recipient lisk address
      - in: query
        name: recipientPublicKey
        description: Recipient public key
      - in: query
        name: senderId
        description: Sender lisk address
      - in: query
        name: senderIdOrRecipientId
        description: Lisk address
      - in: query
        name: senderPublicKey
        description: Sender public key
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: toTimestamp
        description: Ending unix timestamp
      - in: query
        name: type
        description: Transaction type (0-7)
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Transactions
      - Data
  /signatures:
    post:
      summary: Submits a signature object to sign multisignature transactions
      description: |-
        Submits signature to sign a multisignature transaction.
        Signature objects can be generated locally either by using Lisk Commander or with Lisk Elements.
      operationId: postSignature
      x-api-path-slug: signatures-post
      parameters:
      - in: body
        name: signature
        description: Signature object to submit to the network
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Submits
      - Signature
      - Object
      - To
      - Sign
      - Multisignature
      - Transactions
  /votes:
    get:
      summary: Requests votes data for an account
      description: |-
        *Attention: At least **one of the filter parameters must be provided.***
        Returns all votes placed by an account.
      operationId: getVotes
      x-api-path-slug: votes-get
      parameters:
      - in: query
        name: address
        description: Address of an account
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: publicKey
        description: Public key to query
      - in: query
        name: secondPublicKey
        description: Second public key to query
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: username
        description: Delegate username to query
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Votes
      - Dataan
      - Account
  /voters:
    get:
      summary: Requests voters data for a delegate
      description: |-
        *Attention: At least **one of the filter parameters must be provided.***
        Returns all votes received by a delegate.
      operationId: getVoters
      x-api-path-slug: voters-get
      parameters:
      - in: query
        name: address
        description: Address of an account
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: publicKey
        description: Public key to query
      - in: query
        name: secondPublicKey
        description: Second public key to query
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: username
        description: Delegate username to query
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Voters
      - Dataa
      - Delegate
  /blocks:
    get:
      summary: Requests blocks data
      description: Search for a specified block in the system.
      operationId: getBlocks
      x-api-path-slug: blocks-get
      parameters:
      - in: query
        name: blockId
        description: Block id to query
      - in: query
        name: generatorPublicKey
        description: Public key of the forger of the block
      - in: query
        name: height
        description: Current height of the network
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: sort
        description: Fields to sort results by
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Blocks
      - Data
  /delegates/{address}/forging_statistics:
    get:
      summary: Requests forging stats by delegate
      description: |-
        By passing an existing delegate address and the desired unix timestamps, you can get its forging statistics within the specified timespan.
        If no timestamps are provided, it will use the timestamps from Lisk epoch to current date.
      operationId: getForgingStatistics
      x-api-path-slug: delegatesaddressforging-statistics-get
      parameters:
      - in: path
        name: address
        description: Lisk address of a delegate
      - in: query
        name: fromTimestamp
        description: Starting unix timestamp
      - in: query
        name: toTimestamp
        description: Ending unix timestamp
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Forging
      - Stats
      - By
      - Delegate
  /delegates/forgers:
    get:
      summary: Requests next forgers data
      description: Returns a list of the next forgers in this delegate round.
      operationId: getForgers
      x-api-path-slug: delegatesforgers-get
      parameters:
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Next
      - Forgers
      - Data
  /delegates:
    get:
      summary: Requests delegates data
      description: Search for a specified delegate in the system.
      operationId: getDelegates
      x-api-path-slug: delegates-get
      parameters:
      - in: query
        name: address
        description: Address of an account
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: publicKey
        description: Public key to query
      - in: query
        name: search
        description: Fuzzy delegate username to query
      - in: query
        name: secondPublicKey
        description: Second public key to query
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: username
        description: Delegate username to query
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Delegates
      - Data
  /node/transactions/{state}:
    get:
      summary: Requests unprocessed transactions data
      description: |-
        By specifying the state of the transactions, you get a list of unprocessed transactions matching this state.
        Search for specific transactions by providing the appropriate parameters.
        If you post a batch of transactions, they will appear in the unprocessed list after a small delay, depending on server load.
      operationId: getPooledTransactions
      x-api-path-slug: nodetransactionsstate-get
      parameters:
      - in: query
        name: id
        description: Transaction id to query
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: recipientId
        description: Recipient lisk address
      - in: query
        name: recipientPublicKey
        description: Recipient public key
      - in: query
        name: senderId
        description: Sender lisk address
      - in: query
        name: senderPublicKey
        description: Sender public key
      - in: query
        name: sort
        description: Fields to sort results by
      - in: path
        name: state
        description: State of transactions to query
      - in: query
        name: type
        description: Transaction type (0-7)
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Unprocessed
      - Transactions
      - Data
  /node/status/forging:
    put:
      summary: Toggles the forging status of a delegate
      description: |-
        *Attention! This is a **private endpoint only authorized to whitelisted IPs.**
        To edit the whitelist, please edit the `forging.access.whitelist` section in `config.json`*<br>
        Upon passing the correct password and publicKey, forging will be enabled or disabled for the delegate of this particular node.
        The password can be generated locally by encrypting your passphrase, either by using Lisk Commander or with Lisk Elements.
      operationId: updateForgingStatus
      x-api-path-slug: nodestatusforging-put
      parameters:
      - in: body
        name: data
        description: Password for decrypting passphrase of delegate with corresponding
          public key
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Toggles
      - Forging
      - Status
      - Of
      - Delegate
    get:
      summary: Requests forging status of a delegate
      description: |-
        *Attention! This is a **private endpoint only authorized to whitelisted IPs.**
        To edit the whitelist, please edit the `forging.access.whitelist` section in `config.json`*<br>
        Responds with the forging status of a delegate on a node.
      operationId: getForgingStatus
      x-api-path-slug: nodestatusforging-get
      parameters:
      - in: query
        name: publicKey
        description: Public key to query
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Forging
      - Status
      - Of
      - Delegate
  /node/status:
    get:
      summary: Requests status data
      description: Returns all current status data of the node, e.g. height and broadhash.
      operationId: getStatus
      x-api-path-slug: nodestatus-get
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Status
      - Data
  /node/constants:
    get:
      summary: Requests constants data
      description: Returns all current constants data on the system, e.g. Lisk epoch
        time and version.
      operationId: getConstants
      x-api-path-slug: nodeconstants-get
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Constants
      - Data
  /peers:
    get:
      summary: Requests peers data
      description: Search for specified peers.
      operationId: getPeers
      x-api-path-slug: peers-get
      parameters:
      - in: query
        name: broadhash
        description: Broadhash of the network
      - in: query
        name: height
        description: Current height of the network
      - in: query
        name: httpPort
        description: Http port of the node or delegate
      - in: query
        name: ip
        description: IP of the node or delegate
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: os
        description: OS of the node
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: state
        description: Current state of the network
      - in: query
        name: version
        description: Lisk version of the node
      - in: query
        name: wsPort
        description: Web socket port for the node or delegate
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Peers
      - Data
  /dapps:
    get:
      summary: Requests dapps data
      description: Search for a specified dapp in the system.
      operationId: getDapps
      x-api-path-slug: dapps-get
      parameters:
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: name
        description: Name to query - Fuzzy search
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: transactionId
        description: Dapp registration transaction ID
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Dapps
      - Data
  /accounts/{address}/multisignature_memberships:
    get:
      summary: Requests multisignature membership data
      description: Searches for the specified multisignature group and responds with
        a list of all members of this particular multisignature group.
      operationId: getMultisignatureMemberships
      x-api-path-slug: accountsaddressmultisignature-memberships-get
      parameters:
      - in: path
        name: address
        description: Lisk address of a multisignature account
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Multisignature
      - Membership
      - Data
  /accounts/{address}/multisignature_groups:
    get:
      summary: Requests multisignature groups data
      description: Searches for the specified account in the system and responds with
        a list of the multisignature groups that this account is member of.
      operationId: getMultisignatureGroups
      x-api-path-slug: accountsaddressmultisignature-groups-get
      parameters:
      - in: path
        name: address
        description: Lisk address of an account
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Multisignature
      - Groups
      - Data
  /accounts:
    get:
      summary: Requests account data
      description: Search for matching accounts in the system.
      operationId: getAccounts
      x-api-path-slug: accounts-get
      parameters:
      - in: query
        name: address
        description: Address of an account
      - in: query
        name: limit
        description: Limit applied to results
      - in: query
        name: offset
        description: Offset value for results
      - in: query
        name: publicKey
        description: Public key to query
      - in: query
        name: secondPublicKey
        description: Second public key to query
      - in: query
        name: sort
        description: Fields to sort results by
      - in: query
        name: username
        description: Delegate username to query
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Account
      - Data