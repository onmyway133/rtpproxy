rtpproxy - Support IP handover
=========
---

Read more https://onmyway133.github.io/blog/Support-IP-handover-in-rtpproxy-for-VoIP-applications/

Use "src_cnt" to track the number of consecutive packets from different address. When this number exceeds THRESHOLD (10 for RTP and 2 for RTCP), I switch to this new address

This way
  - Client can ALWAYS change IP when he switches from 3G to Wifi, or from this Wifi hotspot to another
  - There's no chance for attack, unless attacker sends > 10 (RTP THRESHOLD) packets in 20ms (supposed my client sends packets every 20ms)

---
This idea is borrowed from  http://www.pjsip.org/pjmedia/docs/html/group__PJMEDIA__CONFIG.htm

There is a macro PJMEDIA_RTP_NAT_PROBATION_CNT. Basically, it is
> "See if source address of RTP packet is different than the configured address, and switch RTP remote address to source packet address after several consecutive packets have been received."

Mobile clients now change IP frequently, from these hotspots to those. So if rtpproxy can support this feature, it would be nicer.


Reference
----
1. http://stackoverflow.com/questions/18200089/how-does-rtpproxy-handle-handover
2. http://lists.sip-router.org/pipermail/sr-users/2008-March/062795.html
3. http://sourceforge.net/p/sippy/rtpproxy/ci/c71201d897ee7c5620d88bb7d56412cd9dc3362a/tree//main.c?diff=5d030295ce90f2f6ff292b0d65bae1d4318db02a

