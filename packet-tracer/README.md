# Cisco Packet Tracer simulation

Place the actual simulation file here as `BoardNet.pkt`.

## Suggested demonstration sequence

1. Open the topology and confirm all interfaces and serial links are up.
2. On routers, use `show ip interface brief` and `show ip route`.
3. On each PC, select DHCP and confirm it receives an address, gateway, and DNS server from the intended service.
4. Test inter-board reachability with `ping`.
5. Open `www.dhk.edu.bd` and `www.ctg.edu.bd` from PCs on multiple boards.
6. Send an email between users on two different board domains.
7. Shut down the DHK–KHU link and verify KHU uses BAR as its alternate path.
8. Restore the link, then shut down the DHK–BAR link and verify BAR uses KHU.
9. Restore all links and save the final topology.

Record actual results and add screenshots under `../screenshots/`. The `.pkt` file was not among the supplied uploads, so this folder is a placeholder until you add it.
