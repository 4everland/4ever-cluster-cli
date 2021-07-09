<h3 align="center">A command line tool for upload file to IPFS Cluster use the IPFS Cluster HTTP API.</h3>

[![NPM Version](https://img.shields.io/npm/v/@4everland/cluster-cli)](https://www.npmjs.org/package/@4everland/cluster-cli)
[![Install Size](https://packagephobia.now.sh/badge?p=@4everland/cluster-cli)](https://packagephobia.now.sh/result?p=@4everland/cluster-cli)
![License](https://img.shields.io/npm/l/@4everland/cluster-cli)


## install

```
npm install -g @4everland/cluster-cli
```

## Command

```
Usage: 4ever-cluster  [options] [command]

Options:
  -V, --version         output the version number
  -h, --help            output usage information

Commands:
  config <arg> [value]  set or show config for host
  add [options] <file>  upload file
```
### **`add`**
```
$ 4ever-cluster  add --help

Usage: 4ever-cluster  [options] <file>

upload file

Options:
  -V, --version        output the version number
  -d, --debug          output extra debugging
  -p, --path <path>    wrapper dir (default: "/")
  --host <host>        ipfs cluster api host (default: "")
  --port <port>        ipfs cluster api port (default: "")
  --showAll            show all file cid
  -t, --token <token>  ipfs cluster api base auth token (default: "")
  -r, --recursive      recursive all sub dir
  -a, --all            include hidden file
  -h, --help           output usage information
```
output data:
```
{
  path: 'web',
  hash: 'QmQPeNsJPyVWPFDVHb77w8G42Fvo15z4bG2X8D2GhfbSXc',
  size: 1042
}
```
or use `--showAll`
```
[
  {
    path: 'web/index.html',
    hash: 'QmQy6xmJhrcC5QLboAcGFcAE1tC8CrwDVkrHdEYJkLscrQ',
    size: 430
  },
  {
    path: 'web/main.css',
    hash: 'QmU5k7ter3RdjZXu3sHghsga1UQtrztnQxmTL22nPnsu3g',
    size: 6
  },
  {
    path: 'web/main.js',
    hash: 'QmYCvbfNbCwFR45HiNP45rwJgvatpiW38D961L5qAhUM5Y',
    size: 6
  },
  {
    path: 'web/sub.html',
    hash: 'QmejvEPop4D7YUadeGqYWmZxHhLc4JBUCzJJHWMzdcMe2y',
    size: 393
  },
  {
    path: 'web',
    hash: 'QmPZ9gcCEpqKTo6aq61g2nXGUhM4iCL3ewB6LDXZCtioEB',
    size: 1042
  }
]
```

`host`, `port`, `token` support load from config file, default config file is `~/.4ever-cluster/conf.yaml`, for example：
```yaml
host: "127.0.0.1"
port: 9094
token: ""
```
The env `_4EVER_CLUSTER_CONF` set custom config file path, for example:
`export _4EVER_CLUSTER_CONF=/custom/path`, the config file is `/custom/path/conf.yaml`.

### **`config`**
```
$ 4ever-cluster config --help
Usage: 4ever-cluster config [options] <arg> [value]

set or show config for host

Arguments:

  arg         the params to set, maybe host、port or token
  value       the value to set

Options:
  -h, --help  output usage information
```
for example, set host: `4ever-cluster  config host "127.0.0.1"`; get current host: `4ever-cluster  config host `

## License

[MIT](LICENSE)
