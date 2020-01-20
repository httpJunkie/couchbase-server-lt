# Build Custom Couchbase Server

```bash
docker pull couchbase
```

Let's clone an existing repo to get a `Dockerfile` and `configuration.sh` file that we can use to build a custom image:

```bash
git clone https://github.com/httpJunkie/couchbase-server-lt && cd couchbase-server-lt && chmod +x configure.sh
```

Build new image from `Dockerfile` which uses official `couchbase` image as its base.

```bash
docker build -t couchbase-server-lt .
```

Run that new image:

```bash
docker run -d -p 8091-8094:8091-8094 -p 11210:11210 -e CB_ADMIN_USER=Administrator -e CB_ADMIN_PASS=123456 -e CB_BUCKET=myBucket CB_BUCKET_PASS= --network="bridge" --name cbslt couchbase-server-lt
```  
  
At this point, we can visit [localhost:8091](http://localhost:8091) and login with the `Administrator` & `123456` username/pass.

We should have 1 server, 1 node, 1 bucket named `myBucket`!
