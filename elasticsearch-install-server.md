1. instalace serveru z DEB repozitáře
 - https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-repositories.html

1. nastavení **/etc/elasticsearch/elasticsearch.yml**
 - ideálně nastavit **cluster.name** a **node.name** pro identifikaci clusteru a nodu
 - nastavit **network.host** podle toho kde má server naslouchat, default je localhost, dají se použít magické konstanty (např. _global_), viz https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-network.html

1. zabezpečení
 - pokud sme dali naslouchat na veřejnou IP, je potřeba zabezpečit na firewallu přístup na porty (default 9200 a 9300) jen z konkrétních IP

1. instalace pluginů (při chybě SSL provést: `update-ca-certificates -f`)
 - `/usr/share/elasticsearch/bin/plugin install mobz/elasticsearch-head`
 - `/usr/share/elasticsearch/bin/plugin install analysis-icu`
 
1. instalace hunspell slovníků
 - https://www.zdrojak.cz/clanky/elasticsearch-vyhledavame-hezky-cesky-ii-a-taky-slovensky/
 - vytvořit strukturu adresářů do `/etc/elasticsearch/hunspell` a nakopírovat do ní soubory, viz předchozí návod, soubory připraveny [zde](https://gitlab.sanasport.cz/doc/elasticsearch-server-install/tree/master/hunspell)
 - oprávnění adresářů i souborů `chown -R root:elasticsearch /etc/elasticsearch/hunspell`
 
1. start
 - `service elasticsearch start`
 - `service elasticsearch status`