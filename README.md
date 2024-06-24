# MOArr
My Own *Arr docker stack definition.

Edit to suit your needs and `docker-compose up -d`. 🚀
> `docker-compose logs -f` at least on first run, just to check everything's ok.

*Arr (aka. Starrs, etc.) is a collection of open-source self-hostable multimedia libraries management apps. They rely on torrent & NZB (usenet) downlaod clients and interconnect with a few other services to build a rich multimedia station.

## Components
### Library management
They arrange your media collections in a beautiful premium-streaming-provider-grade fashion. They also allow you to add entries to download queue through download clients (+ many other features that I don't make use of yet).

- **[Radarr](https://radarr.video/)** : Movies
- **[Sonarr](https://sonarr.tv/)** : TV shows
- **[Bazarr](https://www.bazarr.media/)** : Subtitles
- **[Lidarr](https://lidarr.audio/)** : Music (checkout soulseek and deemix too)
- **[Readarr](https://readarr.com/)** : Books
- **[Whisparr](https://whisparr.com/)** : Bonk ! You go to horny jail.
- etc.

### Indexers proxy
This sexy mofo acts as an aggregator and proxy to a list of torrents/NZB indexers. It embeds a huge collection of public/semi-private/private indexers (w/ up-to-date URLs 😍).

How it works :
- takes a query as input (such as "star wars clone wars")
- builds URLs and query for each selected/configured indexers
- parses the result outputs
- selects the most accurate torrents based on various criterias (pertinence, user-defined priority, desired quality, seeders, etc.)
- Feeds them to your download clients

This drasticaly reduces the hassle of spending hours searching the good torrent/nzb in a dozen of indexers with monthly DNS changes, dead torrents, etc.

- **[Prowlarr](https://prowlarr.com/)**
- **[Jackett](https://github.com/Jackett/Jackett)**
- etc.

They have seamless integration with *Arr apps so the selected indexers can be synced across all apps.

### Download clients
Well, those are classic torrents/NZB clients :
- **[qBittorrent](https://www.qbittorrent.org/)**
- **[Transmission](https://transmissionbt.com/)**
- **[Deluge](https://deluge-torrent.org/)**
- **[Vuze](http://www.vuze.com/)**
- **[NZBget](https://nzbget.net/)**
- **[SABnzbd](https://sabnzbd.org/)**
- etc.

Once files are downloaded, the appropriate library manager "moves" them so they become available in both through library manager and media player.

> By default, files aren't moved nor copied as it would either :
> - be very slow and limit or break torrents seeding
> - or be storage inefficient (use twice the required storage space)
> 
> Instead, library managers use [hardlinks](https://fr.wikipedia.org/wiki/Lien_physique) (see [below](#useful-resources)).

Some of them offer great feature, but not so great UI. Thus, I tend to use an alternative app just for torrent client UI :
- **[Flood](https://flood.js.org/)**
- **[VueTorrent](https://github.com/VueTorrent/)** (No pre-built docker image yet)
- etc.

### Media player
Self-explanatory.
- **[Jellyfin](https://jellyfin.org/)**
- **[Emby](https://emby.media/)** (closed-source)
- **[Plex](https://www.plex.tv/)** (closed-source and requires account 🤮)
- etc.

### Other
- **[Homarr](https://homarr.dev/)** : a dashboard for all those apps. Some alternatives are [Homepage](https://github.com/gethomepage/homepage), [Heimdall](https://github.com/linuxserver/Heimdall), [Homer](https://github.com/bastienwirtz/homer), [Organizr](https://github.com/causefx/Organizr), [Dashy](https://github.com/lissy93/dashy), [Fenrus](https://github.com/revenz/Fenrus) and [Flame](https://github.com/pawelmalak/flame).
- **[FlareSolverr](https://github.com/FlareSolverr/FlareSolverr)** : A CloudFlare anti-bot/ddos bypass (many indexers are cloudflare-protected).
- **[Traefik](https://traefik.io/traefik/)** : Reverse proxy. Some alternatives are [Caddy](https://caddyserver.com/) (arguably better than Traefik, might give it a try later), [NGINX](https://nginx.org/) and [HAProxy](https://www.haproxy.org/).
- **[GlueTun](https://github.com/qdm12/gluetun)** : VPN Client w/ WireGuard support and integrated killswitch.

### Notes
In order to work properly, this setup requires :
- a precise folder structure (see [below](#useful-resources))
- a solid understanding of docker volumes (and docker/docker-compose ecosystem)
- a bunch of time to configure services and their interconnections

## Useful resources
- https://trash-guides.info
- https://wiki.servarr.com
- https://github.com/Ravencentric/awesome-arr
- https://github.com/GreenFrogSB/LMDS

## Roadmap
- add reverse proxy (traefik) for TLS endpoint, subdomain (or subpath) access to services.
- add VPN client w/ killswitch (gluetun) for outbound traffic

**Disclaimer** : For educational purpose only, _[insert random words sequence here]_. Nobody reads this anyway. If you do, find a hobby ffs.

Heave ho ! 🏴‍☠️
