### Twitch
- Expose the Relay chat, allow servers to read/write
- Chatbot websocket servers as datasources for streamer to listen handled events in the realtime.
- Twitch event sub: are publishing events via HTTP/Websocket for subscribed applications for events that we cannot get via IRC, the data's mostly from the streamer data

### Server
- Forward raw events to the SQS/Redis/Kafka for later processing
- Processors handle heavy works, publish result to the Redis channel before fanning out to the Websocket worker
- Websocket worker as the source of the OBS stream
![[Twitch BOT.excalidraw|800x800]]
