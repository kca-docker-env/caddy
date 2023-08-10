# Information about OPKG package(s)

> **Note**: https://wiki.vuplus-support.org/index.php?title=Paketmanager_opkg 

* ```control``` (diese Datei muss enthalten sein),
* ```conffiles``` (optional Datei mit einer Liste von Konfigurationsfiles, die nicht überschrieben werden sollen; pro Zeile ein Filename - wird z.B. im Paket "base-files" benutzt, siehe /var/lib/opkg/info/base-files.* auf der Box)
* ```preinst```, ```prerm``` (optional, Shellscripten, die vor dem installieren bzw. löschen ausgeführt werden)
* ```postinst```, ```postrm``` (optional, Shellscripten, die nach dem installieren bzw. löschen ausgeführt werden)


# Generate Diffie-Hellman key-pair at controller shell

```bash
openssl dhparam -out dhparams.pem 4096
```
