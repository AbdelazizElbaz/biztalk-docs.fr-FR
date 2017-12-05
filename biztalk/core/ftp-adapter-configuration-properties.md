---
title: "Propriétés de Configuration de l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, adapters
- FTP adapters, properties
- FTP adapters, code sample
- FTP adapters, send ports
- FTP adapters, receive locations
- send ports, adapters
ms.assetid: 88a2084e-cb26-4136-9077-8b9463062ccc
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29124c17603abbc9b38a078238d13cdfb1c992e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="ftp-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur FTP
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur FTP :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet à l'emplacement surveillé par l'emplacement de réception.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|serverAddress|VT_BSTR|Indiquer le nom de serveur ou l'adresse IP du serveur FTP.|Aucune|Aucune|  
|serverPort|VT_BSTR|Indiquer le port TCP sur lequel communiquer avec le serveur FTP cible.|Aucune|Aucune|  
|userName|VT_BSTR|Spécifiez le nom d’utilisateur qui est utilisé pour accéder au serveur FTP.|Aucune|Aucune|  
|password|VT_BSTR|Indiquer le mot de passe permettant d'accéder au serveur FTP.|Cette valeur est toujours masquée lors de l'exportation d'un fichier de liaison. Cette propriété doit être renseignée manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
|fileMask|VT_BSTR|Indiquer le filtre de masque de fichier à utiliser pour la transmission des fichiers. |Aucune|Aucune|  
|targetFolder|VT_BSTR|Indiquer l'emplacement d'interrogation sur le serveur FTP.|Aucune|Aucune|  
|commandLogFilename|VT_BSTR|Indiquez l'emplacement d'enregistrement d'une copie du fichier journal.|Aucune|Ce fichier permet de diagnostiquer les conditions d’erreur lors de l’envoi ou réception de fichiers via l’adaptateur FTP.|  
|representationType|VT_BSTR|Permet de sélectionner les modalités de réception des données via l'adaptateur FTP.|Les valeurs valides sont :<br /><br /> -Binaire<br />-ASCII|La valeur par défaut est Binaire.|  
|spoolingFolder|VT_BSTR|Indiquer l'emplacement d'un dossier temporaire sur le serveur FTP. Cette propriété permet de garantir la récupération en cas d'échec de transfert.|Aucune|Aucune|  
|receiveDataTimeOut|VT_BSTR|Indiquer le délai (en millisecondes) avant l'abandon de l'appel de réception. Cette propriété permet d'empêcher qu'un emplacement de réception soit bloqué en raison d'un serveur lent.|Aucune|La valeur par défaut est 90000.|  
|maximumBatchSize|VT_BSTR|Indiquer le nombre maximal d'octets par lot BizTalk Server.|Aucune|Aucune|  
|maximumNumberOfFiles|VT_BSTR|Indiquer le nombre maximal de fichiers par lot BizTalk Server.|Aucune|Aucune|  
|passiveMode|VT_BSTR|Indiquez le mode utilisé par l'adaptateur pour se connecter au serveur FTP.|Les valeurs valides sont :<br /><br /> -Passif<br />-Active|La valeur par défaut est Actif.|  
|useNLST|VT_BSTR|Définir ce paramètre sur Oui pour récupérer uniquement les noms de fichier au lieu de la liste de fichiers par défaut définie par le système|Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Non.|  
|beforeGet|VT_BSTR|Indiquer les commandes FTP à exécuter avant l'obtention du fichier.|Séparez les commandes par un point-virgule ( ;) **Remarque :** commande QUIT n’est pas prise en charge avant l’obtention du fichier.|Aucune|  
|afterGet|VT_BSTR|Indiquer les commandes FTP à exécuter après l'obtention du fichier.|Séparez les commandes par un point-virgule (;)|Aucune|  
|firewallType|VT_BSTR|Indiquer le type de pare-feu déployé.|Les valeurs valides sont :<br /><br /> -Aucun<br />-Socks 4<br />-Socks 5|La valeur par défaut est Aucun.|  
|firewallAddress|VT_BSTR|Spécifiez l’adresse du pare-feu (nom DNS ou adresse IP).|Aucune|Aucune|  
|firewallPort|VT_BSTR|Indiquer le port du pare-feu.|Les valeurs valides vont de 1 à 65535.|La valeur par défaut est 21.|  
|firewallUserName|VT_BSTR|Indiquer le nom d'utilisateur associé au pare-feu.|Aucune|Aucune|  
|firewallPassword|VT_BSTR|Indiquer le mot de passe du pare-feu.|Aucune|Aucune|  
|pollingUnitOfMeasure|VT_BSTR|Indiquer le type d'unité de la propriété pollingInterval.|Les valeurs valides sont :<br /><br /> -Secondes<br />-Minutes<br />-Heures<br />-Jours d’utilisation|La valeur par défaut est Secondes.|  
|pollingInterval|VT_BSTR|Spécifiez la valeur d’intervalle d’interrogation de cet emplacement.|Aucune|Pour effectuer une interrogation de façon permanente, définissez cette valeur sur 0.<br /><br /> La valeur par défaut est 60.|  
|redownloadInterval|VT_BSTR|Intervalle, en secondes, au bout duquel l'adaptateur FTP télécharge de nouveau le fichier.|Cette propriété s'applique uniquement si les propriétés deleteAfterDownload et enableTimeComparison sont définies sur Non.|La valeur -1 indique que l'adaptateur ne téléchargera pas les fichiers de nouveau.<br /><br /> La valeur par défaut est -1.|  
|ssoAffiliateApplication|VT_BSTR|Indiquer l'application associée à l'authentification unique (SSO).|Aucune|Aucune|  
|errorThreshold|VT_BSTR|Indiquer le nombre d'erreurs que le serveur BizTalk Server peut rencontrer avant que l'emplacement ne soit désactivé.|Aucune|La valeur par défaut est 10.|  
|maxFileSize|VT_BSTR|Indiquer la taille maximale de téléchargement des fichiers (en Mo).|Aucune|La valeur 0 indique que la taille des fichiers n'est pas limitée.<br /><br /> La valeur par défaut est 100.|  
|useSsl|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur FTP doit utiliser SSL lors de la communication avec le serveur FTPS.|Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Non.|  
|useDataProtection|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur FTP doit utiliser le chiffrement SSL lors de l'envoi et de la réception de fichiers à partir du serveur FTPS.|Cette propriété est valide si la propriété useSsl est définie sur Oui.<br /><br /> Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Oui.|  
|ftpsConnMode|VT_BSTR|Spécifier le mode de connexion SSL au serveur FTPS.|Les valeurs valides sont :<br /><br /> -Explicite<br />-Implicite|La valeur par défaut est Explicite.|  
|clientCertificateHash|VT_BSTR|Spécifier le hachage SHA1 du certificat client qui doit être utilisé dans la négociation SSL.|Aucune|Selon ce hachage, le certificat client est récupéré dans le magasin personnel du compte d'utilisateur sous lequel l'instance de l'hôte de BizTalk est exécutée.|  
|deleteAfterDownload|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur doit supprimer le fichier à partir du serveur FTP après avoir terminé le téléchargement.|Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Oui.|  
|enableTimeComparison|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur doit de nouveau télécharger un fichier lorsqu'une modification est apportée à l'horodatage de ce fichier.|Cette propriété n'est valide que si la propriété deleteAfterDownload est définie sur Non.<br /><br /> Le serveur FTP cible doit prendre en charge la commande MDTM pour activer cette fonctionnalité.<br /><br /> Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Non.|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>ftp://localhost:21/in/*.xml</uri><serverAddress>localhost</serverAddress><serverPort>21</serverPort><userName>domain\testuser</userName><password>******</password><fileMask>*.xml</fileMask><targetFolder>in</targetFolder><commandLogFilename>c:\temp\realftplog.txt</commandLogFilename><representationType>binary</representationType><maximumBatchSize>0</maximumBatchSize><maximumNumberOfFiles>0</maximumNumberOfFiles><passiveMode>False</passiveMode><firewallType>NoFirewall</firewallType><firewallPort>21</firewallPort><pollingUnitOfMeasure>Seconds</pollingUnitOfMeasure><pollingInterval>5</pollingInterval><errorThreshold>10</errorThreshold><maxFileSize>5000</maxFileSize><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><deleteAfterDownload>True</deleteAfterDownload><enableTimeComparison>False</enableTimeComparison></Config></AdapterConfig></CustomProps>  
```  
  
 Ce tableau répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur FTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet de l'emplacement de réception des données.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|serverAddress|VT_BSTR|Indiquer l'adresse du pare-feu, à savoir un nom DNS ou une adresse IP.|Aucune|Aucune|  
|serverPort|VT_BSTR|Spécifier l'adresse du port du serveur FTP.|Aucune|La valeur par défaut est 21.|  
|userName|VT_BSTR|Indiquer le nom d'utilisateur pour la connexion au serveur FTP.|Aucune|Aucune|  
|password|VT_BSTR|Spécifier le mot de passe de connexion au serveur FTP.|Cette valeur est toujours masquée lors de l'exportation d'un fichier de liaison. Cette propriété doit être renseignée manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
|accountName|VT_BSTR|Indiquer le nom du compte pour le serveur FTP.|Ce paramètre est facultatif|Aucune|  
|targetFolder|VT_BSTR|Indiquer l'emplacement vers lequel déplacer les fichiers sur le serveur FTP.|Aucune|Aucune|  
|targetFileName|VT_BSTR|Indiquer un autre nom pour le fichier. Conserver le nom par défaut garantit l'unicité des noms de message pour chaque message envoyé. |Aucune|La valeur par défaut est %MessageID%.xml.|  
|commandLogFilename|VT_BSTR|Indiquez l'emplacement d'enregistrement d'une copie du fichier journal. Ce fichier journal permet de diagnostiquer les conditions d'erreur lors de l'envoi ou de la réception de fichiers via un serveur FTP.|Aucune|Aucune|  
|representationType|VT_BSTR|Sélectionner la méthode utilisée par FTP pour l'envoi de données (au format binaire ou ASCII).|Les valeurs valides sont :<br /><br /> -binaire<br />-ASCII|La valeur par défaut est binaire.|  
|beforePut|VT_BSTR|Indiquer les commandes FTP à exécuter avant le placement du fichier, telles que les commandes permettant de modifier les valeurs par défaut sur le serveur FTP.|Séparez les commandes par un point-virgule (;). **Remarque :** commande QUIT n’est pas prise en charge avant le placement du fichier.|Aucune commande Ouvrir n'est requise.|  
|afterPut|VT_BSTR|Indiquer les commandes FTP à exécuter après le fichier PUT.|Séparez les commandes par un point-virgule (;).|Aucune|  
|allocateStorage|VT_BSTR|Indiquer si de l'espace de stockage doit être alloué pour les systèmes hôtes existants.|Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Non.|  
|spoolingFolder|VT_BSTR|Indiquer l'emplacement d'un dossier temporaire sur le serveur FTP. Cette propriété permet de garantir la récupération en cas d'échec de transfert si le mode de transfert est binaire. Si le mode de transfert est ASCII, l'adaptateur redémarre le téléchargement.|Aucune|Aucune|  
|connectionLimit|VT_BSTR|Spécifier un nombre maximal de connexions FTP simultanées pouvant être établies vers le serveur.|Aucune|La valeur 0 indique une absence de limite.|  
|passiveMode|VT_BSTR|Indiquer s'il faut utiliser le mode passif ou actif.|Les valeurs valides sont :<br /><br /> -La valeur true (mode passif)<br />-False (mode actif)|La valeur par défaut est False (mode actif).|  
|firewallType|VT_BSTR|Sélectionner le type de pare-feu déployé.|Les valeurs valides sont :<br /><br /> -Socks 4<br />-Socks 5<br />-Aucun|La valeur par défaut est Aucun.|  
|firewallAddress|VT_BSTR|Indiquer l'adresse du pare-feu, à savoir un nom DNS ou une adresse IP.|Aucune|Aucune|  
|firewallPort|VT_BSTR|Indiquer le port du pare-feu.|Les valeurs valides vont de 1 à 65535.|La valeur par défaut est 21.|  
|firewallUserName|VT_BSTR|Indiquer le nom d'utilisateur associé au pare-feu.|Aucune|Aucune|  
|firewallPassword|VT_BSTR|Indiquer le mot de passe du pare-feu.|Cette valeur est toujours masquée lors de l'exportation d'un fichier de liaison. Cette propriété doit être renseignée manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
|ssoAffiliateApplication|VT_BSTR|Indiquer l'application associée à l'authentification unique (SSO).|Aucune|Aucune|  
|useSsl|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur FTP doit utiliser SSL lors de la communication avec le serveur FTPS.|Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Non.|  
|useDataProtection|VT_BSTR|Définir ce paramètre sur Oui si l'adaptateur FTP doit utiliser le chiffrement SSL lors de l'envoi et de la réception de fichiers à partir du serveur FTPS.|Cette propriété est valide si la propriété useSsL est définie sur Oui.<br /><br /> Les valeurs valides sont :<br /><br /> -Oui<br />-Non|La valeur par défaut est Oui.|  
|ftpsConnMode|VT_BSTR|Spécifier le mode de connexion SSL au serveur FTPS.|Les valeurs valides sont :<br /><br /> -Explicite<br />-Implicite|La valeur par défaut est Explicite.|  
|clientCertificateHash|VT_BSTR|Spécifiez le hachage SHA1 du certificat client qui doit être utilisé dans la négociation SSL.|Aucune|Selon ce hachage, le certificat client est récupéré dans le magasin personnel du compte d'utilisateur sous lequel l'instance de l'hôte de BizTalk est exécutée.|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><serverAddress>TestServer</serverAddress><serverPort>21</serverPort><userName>testuser</userName><password>******</password><accountName>testuser</accountName><targetFolder>output</targetFolder><targetFileName>%MessageID%.xml</targetFileName><commandLogFilename>c:\logfile\ftpsendlog.txt</commandLogFilename><representationType>binary</representationType><beforePut>CDW dir</beforePut><afterPut>CDUP </afterPut><allocateStorage>False</allocateStorage><spoolingFolder>tempfolder</spoolingFolder><connectionLimit>0</connectionLimit><passiveMode>False</passiveMode><firewallType>Socks4</firewallType><firewallAddress>TestServer</firewallAddress><firewallPort>21</firewallPort><firewallUserName>domain\testuser</firewallUserName><firewallPassword>******</firewallPassword><useSsl>False</useSsl><useDataProtection>True</useDataProtection><ftpsConnMode>Explicit</ftpsConnMode><clientCertificateHash>‎bc 32 2c a9 22 75 6a 3f e4 f7 a9 b1 b3 3a 24 20 23 53 68 49</clientCertificateHash><uri>ftp://TestServer:21/output/%MessageID%.xml</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  Lorsque vous spécifiez les données de configuration TransportTypeData pour un adaptateur créé à l’aide de l’infrastructure d’adaptateurs, toutes les paires nom/valeur utilisées doivent être stockés dans le \<AdapterConfig\> élément. Étant donné que le \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données, puis le \< \> caractères dans les données doivent être échappés.