# Some Shadowtraffic Notes.

So I have a larger project MongoCreator where in Iuse a custom Golang application to create 2 sets of documents posted onto Kafka Topics. well it's over a 1000 lines... Learned allot writing it...

    - https://medium.com/@georgelza/an-exercise-in-discovery-streaming-data-in-the-analytical-world-part-1-e7c17d61b9d2
    - https://github.com/georgelza/MongoCreator-GoProducer-avro.git


But, Shadowtraffic will allow me to accomplish the same inside a compact docker container using a input config file.
Simplying things allot.


- https://shadowtraffic.io

- https://www.youtube.com/playlist?list=PLB8as4ufg7p9xii07ZM0sfPsLfq1j-vLe

- https://chatgpt.com/share/34e8a7e8-9646-48d3-b67e-b08e45b42016


##  Step 1 to figure things out before using the above service.

Navigate to http://localhost:9876

docker run  \
    --name shadow \
    -p 9876:8080 \
    -v $(pwd)/conf/avro-retail.json:/workspace/config.json \
    -v $(pwd)/conf/clerks.json:/workspace/clerks.json \
    -v $(pwd)/conf/stores.json:/workspace/stores.json \
    -v $(pwd)/conf/basketItems.json:/workspace/basketItems.json \
    --env-file $(pwd)/conf/license.env \
    --env-file $(pwd)/conf/params.env \
    shadowtraffic/shadowtraffic:latest \
    --config /workspace/config.json \
    --with-studio \
    --watch --sample 10 --stdout --watch 


