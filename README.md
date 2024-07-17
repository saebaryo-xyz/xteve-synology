# xteve-synology
Installation guide for Xteve IPTV Proxy on Synology with Docker

# Reuirements

1. Any Synology Hardware
2. Install Docker from the Package Center

# Steps:

1. Task Scheduler
2. General > Xteve Install. User > root
3. Scheduler > RUn on the following date and leave as is
4. Task settings > Paste the installation script:
   docker run -it -d \
  --name=xteve \
  --network=host \
  --restart on-failure:3 \
  -e PUID=1026 \
  -e PGID=100 \
  -e TZ=Europe/Vilnius \
  -v /volume1/docker/xteve:/home/xteve/conf \
  dnsforge/xteve:latest
5. Click on OK, then right click on it and "Run".
6. Give it 3-5 mns
7. Access from: yournas-ip-address:34400/web
8. Choose XEPG option when prompted in xteve
9. Add the M3U URL when prompted (Example format: http://your-iptv-provider-domainname:port/get.php?username=iptvusername&password=iptvpassword&type=m3u_plus)
10. Add the XML file as well (Example format: http://your-iptv-provider-domainname:port/xmltv.php?username=iptvusername&password=iptvpassword&type=m3u_plus)
11. Now to Jellyfinm Plex or Emby > Go to your Live TV settings (depending on the tool you choose) > Tuner Device > Choose "M3U Tuner"
12. Add your-server-ip:34400/m3u/xteve.m3u
13. Go to TV Guide provider (Relevant to Jellyfin, not sure if relevant to Plex/Emby)
14. Add the XML TV Guide: your-server-ip:34400
15. Click on Refresh Guide Data
16. Go to your Live TV in the main menu and you should see channels and their EPG.
17. Enjoy!

