{
  "dns" : {
    "queryStrategy" : "UseIP",
    "servers" : [
      {
        "address" : "77.88.8.8",
        "domains" : [
          "geosite:category-ru",
          "domain:ru",
          "domain:su",
          "domain:рф",
          "keyword:dixy",
          "keyword:mts"
        ]
      },
      "1.1.1.1",
      "1.0.0.1"
    ]
  },
  "inbounds" : [
    {
      "listen" : "127.0.0.1",
      "port" : 10808,
      "protocol" : "socks",
      "settings" : {
        "auth" : "noauth",
        "udp" : true
      },
      "sniffing" : {
        "destOverride" : [
          "http",
          "tls",
          "quic"
        ],
        "enabled" : true,
        "routeOnly" : false
      },
      "tag" : "socks"
    },
    {
      "listen" : "127.0.0.1",
      "port" : 10809,
      "protocol" : "http",
      "settings" : {
        "allowTransparent" : false
      },
      "sniffing" : {
        "destOverride" : [
          "http",
          "tls",
          "quic"
        ],
        "enabled" : true,
        "routeOnly" : false
      },
      "tag" : "http"
    }
  ],
  "log" : {
    "access" : "\/private\/var\/mobile\/Containers\/Shared\/AppGroup\/0782FD52-97A0-49D1-8263-8BC708856136\/Library\/Application Support\/Xray\/logs\/access.log",
    "dnsLog" : true,
    "loglevel" : "Warning"
  },
  "outbounds" : [
    {
      "protocol" : "vless",
      "settings" : {
        "vnext" : [
          {
            "address" : "84.201.135.143",
            "port" : 443,
            "users" : [
              {
                "encryption" : "none",
                "flow" : "xtls-rprx-vision",
                "id" : "e0025cfe-1ed0-4a97-af57-6a4f009eb9b7"
              }
            ]
          }
        ]
      },
      "streamSettings" : {
        "network" : "tcp",
        "realitySettings" : {
          "fingerprint" : "chrome",
          "publicKey" : "orVWsMho33Zn5AMeZB8009TCky2hZDITYdChy-aZdgY",
          "serverName" : "ads.x5.ru",
          "shortId" : "c6e7589810a87a42"
        },
        "security" : "reality",
        "tcpSettings" : {

        }
      },
      "tag" : "proxy"
    },
    {
      "protocol" : "freedom",
      "tag" : "direct"
    },
    {
      "protocol" : "blackhole",
      "tag" : "block"
    }
  ],
  "remarks" : "🇷🇺 Обход (ВСЕ ОПЕРАТОРЫ)",
  "routing" : {
    "domainMatcher" : "hybrid",
    "domainStrategy" : "IPIfNonMatch",
    "rules" : [
      {
        "domain" : [
          "geosite:category-ru",
          "domain:ru",
          "domain:su",
          "domain:рф"
        ],
        "ip" : [
          "geoip:ru",
          "geoip:private"
        ],
        "outboundTag" : "direct",
        "type" : "field"
      },
      {
        "outboundTag" : "direct",
        "protocol" : [
          "bittorrent"
        ],
        "type" : "field"
      }
    ]
  }
}
