# Some Shadowtraffic Notes.

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


