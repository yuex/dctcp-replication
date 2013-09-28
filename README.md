# DCTCP Replication

This project is initially created for the replication of DCTCP in 2011.
NOTE: There are some dirty hacks and hard coding in it. My faults. In general, it's still very primitive.  But I think make it public may help someone on the replication of DCTCP or other similar work.

# Workflow

Save IP of your nodes in `ipf` or other file you like, but use it consistently.

To generate short and background flows described in DCTCP

    ./trafficgen.sh gen ipf traffic_dir

Upload it to your hosts, needs ssh configured using key authentication

    ./trafficgen.sh upload ipf traffic_dir

Start daemons for experiment

    ./trafficgen.sh exec ipf startserver

Configure node to turn on dctcp_enable, do it on every node

    sysctl -w net.ipv4.tcp_dctcp_enalbe=1

Told daemons on nodes to start sending flows

    ./benchmarkstart.sh ipf

Collect, clean and summarize logs

    ./getlog.sh
    ./striplog.sh your_log_summary

Do what ever analysis you what to these log. They are your men

Also, steps above are summarized into `justdoit.sh`, configure some parameters in `justdoit.conf` to suit your needs
