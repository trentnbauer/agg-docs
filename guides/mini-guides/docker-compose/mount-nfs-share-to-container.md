# Mount NFS Share to Container



<pre class="language-yaml" data-title="docker-compose.yml"><code class="lang-yaml"><strong>version: "2.3"
</strong>services:
  app:
    image: myimage
    volumes:
      - nfs:/container/path
....

volumes:
  nfs:
    driver_opts:
      type: "nfs"
      o: addr=$NFSSERV,nfsvers=4
      device: $NFSPATH
</code></pre>

{% code title=".env" %}
```
NFSSERV=fully.qualified.domain or IP address of NFS server
$NFSPATH=:/Path/To/NFS/Share
```
{% endcode %}
