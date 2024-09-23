This can be used when we are auditing logs from UI application and storing in mongo. but due to some memory constrint, we need to store logs for certsin period of time only.
In MongoDB, you can set a TTL (Time-to-Live) for records in a collection using a TTL index. A TTL index will automatically remove documents from a collection after a specified
amount of time.
Here’s how you can set a TTL index:
  1. Add a Date Field
  First, you need to add a date field to your documents that MongoDB will use to determine when the document should expire. For example, you can add a field called createdAt.
      {
        "_id": ObjectId("64a1f3f1234567890"),
        "createdAt": ISODate("2024-09-23T14:00:00Z"),
        "data": "some document data"
      }
2. Create a TTL Index
You then create a TTL index on the createdAt field with a specified expiration time in seconds. For example, if you want to delete documents 1 hour (3600 seconds) after their
createdAt time, you can do this using the following command:
    db.collection.createIndex(
       { "createdAt": 1 },
       { expireAfterSeconds: 3600 }
    )
Notes:
The TTL index only works on fields that contain a BSON Date value.
The background process that removes expired documents runs every 60 seconds by default, so there might be a slight delay between when a document is eligible
for deletion and when it is actually removed.
Once the TTL index is set, documents will be automatically removed, without needing to write manual deletion logic.

########################################################################################################################################################################################


CACHING - SYSTEM DESIGN
Good Cache gives you Faster Systems.
Bad Cache gives you Wrong Data.
Here are the 5 things you need to handle Cache Expiration.

𝟭. 𝗗𝗲𝗳𝗶𝗻𝗲 𝗮𝗻 𝗘𝘅𝗽𝗶𝗿𝗮𝘁𝗶𝗼𝗻 𝗧𝗶𝗺𝗲
Decide how long cached data remains valid. This timeframe depends on the nature of your data and how frequently it changes. If you're caching flight status,
a shorter expiration time (5 min) might be suitable, as customers need accurate info. But a longer expiration time could suffice if you're caching weather forecasts.

𝟮. 𝗧𝗶𝗺𝗲𝘀𝘁𝗮𝗺𝗽 𝗼𝗿 𝗧𝗧𝗟 (𝗧𝗶𝗺𝗲-𝘁𝗼-𝗟𝗶𝘃𝗲)
Associate each cached entry with a timestamp or a Time-to-Live (TTL) value. A timestamp indicates when the data was cached, while a TTL specifies the duration
for which the data remains valid. If the data has expired, then it's requested again.

𝟯. 𝗖𝗵𝗲𝗰𝗸 𝗘𝘅𝗽𝗶𝗿𝘆 𝗼𝗻 𝗔𝗰𝗰𝗲𝘀𝘀
Before returning cached data, check its timestamp or TTL. If the data has exceeded its expiration time, it could be stale and should be refreshed.

𝟰. 𝗥𝗲𝗳𝗿𝗲𝘀𝗵 𝗠𝗲𝗰𝗵𝗮𝗻𝗶𝘀𝗺
When you detect expired data, trigger a refresh mechanism. Fetch the latest data from the source and update the cache with the new information.
So, the next requests can access the refreshed, accurate data.

𝟱. 𝗚𝗿𝗮𝗰𝗲𝗳𝘂𝗹 𝗗𝗲𝗴𝗿𝗮𝗱𝗮𝘁𝗶𝗼𝗻
When refreshing data takes longer than expected, make sure your application handles it. Displaying slightly outdated data is often better than presenting no data at all.

The idea is to find the right balance between freshness and efficiency. Handling cache expiration guarantees that your users receive accurate and relevant data.
