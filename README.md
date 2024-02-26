# IBC Task shielded-expedition.88f17d1d14

Nebb player:

https://extended-nebb.kintsugi.tech/player/tpknam1qq2lhj5mllyl9tdgcavaqvwfk4yn5lqcrvp62lewrxffvk9yuphcve9e0j8

Osmosis IBC wallet:

https://www.mintscan.io/osmosis-testnet/address/osmo1aml3kvzcj7utuusysyyttjnhsfkgr09vrhyzr0

Namada IBC wallet:

tnam1qpljcwzq5tpfnkz59w29zk4fh2l4r6dhgslayccu
```
Transaction transfer:

TX Hash: 8072A17CB934EE252275AFEE08BFC25643E485BC26754D10993F589805C37856
Wrapper Hash: 7520D672F8DB87D2835BCE9A9831F273E7E0A2568F21A3155731AF91D5CBA157
Block ID: 58FD33AB9647C40D8B059BBF6FEE64F410C0EDF32DD73E205337324953F0BA8B

From: tnam1qzapwdp5ldskua87lqd0nd2kcc7pjeljvqxt770v
To: tnam1qpljcwzq5tpfnkz59w29zk4fh2l4r6dhgslayccu
Token: tnam1qxvg64psvhwumv3mwrrjfcz0h3t3274hwggyzcee
Amount: 100.000000
```

## Create channel Namada <> Osmosis

```
hermes create channel \
  --a-chain shielded-expedition.88f17d1d14 \
  --b-chain osmo-test-5 \
  --a-port transfer \
  --b-port transfer \
  --new-client-connection --yes
```
```
SUCCESS Channel {
    ordering: Unordered,
    a_side: ChannelSide {
        chain: BaseChainHandle {
            chain_id: ChainId {
                id: "shielded-expedition.88f17d1d14",
                version: 0,
            },
            runtime_sender: Sender { .. },
        },
        client_id: ClientId(
            "07-tendermint-1766",
        ),
        connection_id: ConnectionId(
            "connection-756",
        ),
        port_id: PortId(
            "transfer",
        ),
        channel_id: Some(
            ChannelId(
                "channel-495",
            ),
        ),
        version: None,
    },
    b_side: ChannelSide {
        chain: BaseChainHandle {
            chain_id: ChainId {
                id: "osmo-test-5",
                version: 5,
            },
            runtime_sender: Sender { .. },
        },
        client_id: ClientId(
            "07-tendermint-2421",
        ),
        connection_id: ConnectionId(
            "connection-2254",
        ),
        port_id: PortId(
            "transfer",
        ),
        channel_id: Some(
            ChannelId(
                "channel-5942",
            ),
        ),
        version: None,
    },
    connection_delay: 0ns,
}
```

### Test transactions:

**`IBC Namada <> Osmosis`**

```
namadac ibc-transfer \
--amount 1 \    
--source ibcwallet \
--signing-keys ibcwallet \
--receiver osmo1aml3kvzcj7utuusysyyttjnhsfkgr09vrhyzr0 \
--token naan \
--channel-id channel-495 \
--memo tpknam1qq2lhj5mllyl9tdgcavaqvwfk4yn5lqcrvp62lewrxffvk9yuphcve9e0j8
```

```
TX Hash: 1FAE5640E14795E2F4A4C23DCF04C3F207DCFB9F2C8ADB7618EFF809527354B9
Wrapper Hash: DCCFB321099F59D565CE8161FB70CF5586E890805AAA7829A987B4B7CCEAF0F3
Block ID: C4209BF133CD87B7D0D781762DEDD14A5107CF093AA9CFD2926E41636E028490

Message: MsgTransfer
```
URL Transaction:
https://www.mintscan.io/osmosis-testnet/tx/0D6433101E0563B9D8132C2639A6957F09B7BC711C44C36F99386947024A5F69?height=5649648



**`IBC Osmosis <> Namada`**

```
hermes tx ft-transfer \
--dst-chain shielded-expedition.88f17d1d14 \
--src-chain osmo-test-5 \
--src-port transfer \
--src-channel channel-5942 \
--amount 1 \
--denom ibc/1EB433F8C2B0AE43A536B83E114DBB7CEA28D5EB091740F4EB5B9AF1A02BFF7B
```

```
SUCCESS [
    IbcEventWithHeight {
        event: SendPacket(
            SendPacket {
                packet: Packet {
                    sequence: Sequence(
                        1,
                    ),
                    source_port: PortId(
                        "transfer",
                    ),
                    source_channel: ChannelId(
                        "channel-5942",
                    ),
                    destination_port: PortId(
                        "transfer",
                    ),
                    destination_channel: ChannelId(
                        "channel-495",
                    ),
                    data: [123, 34, 97, 109, 111, 117, 110, 116, 34, 58, 34, 49, 34, 44, 34, 100, 101, 110, 111, 109, 34, 58, 34, 116, 114, 97, 110, 115, 102, 101, 114, 47, 99, 104, 97, 110, 110, 101, 108, 45, 53, 57, 52, 50, 47, 116, 110, 97, 109, 49, 113, 120, 118, 103, 54, 52, 112, 115, 118, 104, 119, 117, 109, 118, 51, 109, 119, 114, 114, 106, 102, 99, 122, 48, 104, 51, 116, 51, 50, 55, 52, 104, 119, 103, 103, 121, 122, 99, 101, 101, 34, 44, 34, 114, 101, 99, 101, 105, 118, 101, 114, 34, 58, 34, 116, 110, 97, 109, 49, 113, 112, 108, 106, 99, 119, 122, 113, 53, 116, 112, 102, 110, 107, 122, 53, 57, 119, 50, 57, 122, 107, 52, 102, 104, 50, 108, 52, 114, 54, 100, 104, 103, 115, 108, 97, 121, 99, 99, 117, 34, 44, 34, 115, 101, 110, 100, 101, 114, 34, 58, 34, 111, 115, 109, 111, 49, 97, 109, 108, 51, 107, 118, 122, 99, 106, 55, 117, 116, 117, 117, 115, 121, 115, 121, 121, 116, 116, 106, 110, 104, 115, 102, 107, 103, 114, 48, 57, 118, 114, 104, 121, 122, 114, 48, 34, 125],
                    timeout_height: Never,
                    timeout_timestamp: Timestamp {
                        time: Some(
                            Time(
                                2024-02-26 23:35:48.443264485,
                            ),
                        ),
                    },
                },
            },
        ),
        height: Height {
            revision: 5,
            height: 5650369,
        },
    },
]

```
URL Transaction:
https://www.mintscan.io/osmosis-testnet/tx/BB5DA5F32A339D0FCC9B021FDE1F539D01203D27DD8492C9F2A7F50CC307C88F?height=5650369
