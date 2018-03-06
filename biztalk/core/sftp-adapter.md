---
title: Adaptateur SFTP | Documents Microsoft
description: "Créer ou configurer un emplacement de réception et envoi du port à l’aide de l’adaptateur SFTP dans BizTalk Server, y compris des questions fréquentes à l’aide de l’adaptateur SFTP"
ms.custom: 
ms.date: 02/26/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f64c4c8-64a0-4e43-9660-b5c2d75d28aa
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d28c3b453ab3e704ddbb06ed42b23dc641a6711
ms.sourcegitcommit: 3bcf85356d43c3502e61fa801316dc12a4547406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2018
---
# <a name="sftp-adapter"></a>Adaptateur SFTP
BizTalk Server inclut un **SFTP** adaptateur pour envoyer et recevoir des messages à partir d’un serveur FTP sécurisé via le protocole de transfert de fichier SSH. Cette rubrique inclut les étapes pour configurer un **SFTP** emplacement de réception et configurer un port d’envoi SFTP pour recevoir et envoyer des messages à partir d’un serveur FTP sécurisé. Il inclut également des questions et réponses.

## <a name="prerequisites"></a>Configuration requise
**À partir de BizTalk Server 2016**, l’adaptateur SFTP WinSCP pour se connecter à SFTP et par conséquent prend en charge un plus grand serveurs de plage de SFTP. **Télécharger [WinSCP](http://winscp.net)**  sur l’exécution de BizTalk Server. Veillez à vérifier les versions prises en charge WinSCP [matérielle et logicielle requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)

BizTalk Server 2013 R2 et versions antérieures ne prennent pas en charge WinSCP.
  
## <a name="configure-the-receive-location"></a>Configurer l’emplacement de réception
  
> [!NOTE]
>  Avant de créer l’emplacement de réception, vous devez avoir déjà ajouté un port de réception unidirectionnel. Consultez [créer un Port de réception](../core/how-to-create-a-receive-port.md) pour connaître les étapes spécifiques.  
  
 
1.  Dans la console Administration de BizTalk Server, développez BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’application sous laquelle créer un emplacement de réception.  
  
2.  Dans le volet gauche, cliquez sur le nœud **Ports de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception auquel vous souhaitez associer le nouvel emplacement de réception, puis cliquez sur **Propriétés**.  
  
3.  Dans le volet gauche de la boîte de dialogue **Propriétés des ports de réception** , sélectionnez **Emplacements de réception**, puis dans le volet droit, cliquez sur **Nouveau** pour créer un emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section, sélectionnez **SFTP** à partir de la **Type** la liste déroulante, puis Cliquez sur **configurer** pour configurer les propriétés de transport pour l’emplacement de réception.  
  
5.  Dans le **propriétés du Transport SFTP**, procédez comme suit :  
 
     **Autres**
         
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Limite de connexions|Spécifier le nombre maximal de connexions simultanées qui peuvent être ouvertes sur le serveur.<br /><br /> Ce paramètre est défini par serveur et par emplacement de réception. Examinez les scénarios suivants :<br /><br /> -Il existe deux emplacements de réception qui ont les mêmes valeurs de propriété de configuration, y compris la propriété ConnectionLimit définie sur la même valeur. Par exemple, la propriété est définie sur 6. Dans ce cas, il existe une seule connexion pool (avec 6 connexions disponibles) qui est utilisé par les deux emplacements de réception.<br /><br /> -Il existe deux emplacements de réception configurés avec les mêmes valeurs et avoir la propriété ConnectionLimit définie sur des valeurs différentes. Par exemple, la propriété ReceiveLocation1 est définie sur 6, et la propriété ReceiveLocation2 est définie à 5. Dans ce cas, chaque emplacement de réception a son propre pool de connexions avec ses propres connexions disponibles. Le pool de connexions ReceiveLocation1 a 6 connexions disponibles. Le pool de connexions ReceiveLocation2 a 5 connexions disponibles.|  
    |Journal | Disponible à partir de BizTalk Server 2016. <br/><br/>Entrez le chemin d’accès complet pour créer un fichier de journal côté client. Utiliser ce fichier journal pour résoudre les erreurs.|
  
     **Interrogation**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Intervalle d’interrogation|Spécifiez les intervalles à laquelle l’adaptateur interroge le serveur. Pour effectuer une interrogation continue, définissez cette valeur sur zéro.<br /><br /> **Valeur par défaut :** 5|  
    |Unité|Spécifie l'unité dans laquelle l'intervalle d'interrogation est exprimé, par exemple, Secondes, Minutes, Heures ou Jours.<br /><br /> **Valeur par défaut :** secondes|  
  
     **Proxy** (disponible en commençant par BizTalk Server 2013 R2)  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Adresse|Indique soit le nom DNS soit l'adresse IP du serveur proxy.|  
    |Mot de passe|Indique le mot de passe du serveur proxy.|  
    |Port|Indique le port du serveur proxy.|  
    |Type|Spécifie le protocole utilisé par le serveur proxy.|  
    |UserName|Indique le nom d'utilisateur du serveur proxy.|  
  
     **Sécurité**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Accepter n’importe quel hôte de serveur SSH|Lorsque **True**, l’emplacement de réception accepte n’importe quelle touche de l’hôte public SSH à partir du serveur. Lorsque **False**, l’emplacement de réception utilise l’empreinte digitale du serveur pour l’authentification. Vous entrez l’empreinte dans le **SSHServerHostKeyFingerPrint** propriété.<br /><br /> **Valeur par défaut :** False|  
    |Mode d’authentification client|Sélectionnez la méthode d’authentification qui utilise de l’emplacement de réception pour l’authentification du client sur le serveur SSH. Si la valeur **mot de passe**, vous devez entrer la valeur dans la **mot de passe** propriété. Si la valeur **PublicKeyAuthentication**, vous devez entrer la clé privée de l’utilisateur dans le **PrivateKey** propriété. Si la valeur **MultiFactorAuthentication** vous devez entrer **nom d’utilisateur** avec son **mot de passe** et **PrivateKey**. En outre, si la clé privée est protégée par un mot de passe, entrez le mot de passe ainsi qu’à la **PrivateKeyPassword** propriété.<br /><br /> **Valeur par défaut :** mot de passe|  
    |Chiffrement |Disponible à partir de BizTalk Server 2013 R2. <br/><br/>Entrez le type d’algorithme de chiffrement.<br/><br/>Options de BizTalk Server 2013 R2 : Auto, AES et TripleDES<br/><br/>Options de BizTalk Server 2016 : automatique, AES, Arcfour, Blowfish, TripleDES et DES|  
    |Mot de passe|Spécifiez le mot de passe utilisateur SFTP si vous définissez la **ClientAuthenticationMode** à **mot de passe**.|  
    |Clé privée|Spécifiez la clé privée pour l’utilisateur SFTP si vous définissez la **ClientAuthenticationMode** à **PublicKeyAuthentication**.<br /><br /> **Remarque :** le fichier de clé privée doit être le fichier .ppk spécifié.|  
    |Mot de passe de clé privée|Spécifiez un mot de passe clé privée, si nécessaire, pour la clé spécifiée dans le **PrivateKey** propriété.|  
    |Hôte du serveur SSH clé par empreinte digitale|Spécifie l'empreinte de la clé de l'hôte public pour le serveur SSH.|  
    |Nom d'utilisateur|Spécifie le nom d'utilisateur de connexion au serveur SFTP.|  
  
     **SSH Server**  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Masque de fichier|Spécifie le masque de fichier à utiliser lors de la récupération de fichiers à partir d'un serveur FTP sécurisé.|  
    |Chemin d’accès du dossier|Spécifie le chemin d'accès du dossier sur le serveur FTP sécurisé à partir duquel l'emplacement de réception peut récupérer des fichiers.|  
    |Port|Spécifie l'adresse de port pour le serveur FTP sécurisé sur lequel le transfert de fichiers a lieu.|  
    |Adresse du serveur|Spécifie le nom ou l'adresse IP du serveur FTP sécurisé.|  
  
6.  Cliquez sur **OK**.  
  
7.  Entrez les valeurs appropriées dans la boîte de dialogue **Propriétés de l'emplacement de réception** pour terminer la configuration de l'emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [créer un emplacement de réception](../core/how-to-create-a-receive-location.md).
 
## <a name="configure-the-send-port"></a>Configurer le port d’envoi  
  
1.  Dans la console Administration de BizTalk Server, créez un port d’envoi ou double-cliquez sur un port d’envoi existant pour le modifier. Pour plus d’informations, consultez [créer un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **SFTP** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** bouton.  
  
3.  Dans le **propriétés du Transport SFTP**, entrez les informations suivantes :  
  
    **Autres**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Limite de connexions|Spécifier le nombre maximal de connexions simultanées qui peuvent être ouvertes sur le serveur.|  
    |Journal | Disponible à partir de BizTalk Server 2016. <br/><br/>Entrez le chemin d’accès complet pour créer un fichier de journal côté client. Utiliser ce fichier journal pour résoudre les erreurs.|
    |Dossier temporaire | Disponible à partir de BizTalk Server 2013 R2. <br/><br/>Dossier temporaire sur le serveur SFTP pour télécharger des fichiers volumineux, avant qu'ils ne puissent être déplacés de façon atomique vers l'emplacement souhaité sur le même serveur.|  
    
    **Proxy** (disponible à partir de BizTalk Server 2013 R2)
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Adresse|Indique soit le nom DNS soit l'adresse IP du serveur proxy.|  
    |Mot de passe|Indique le mot de passe du serveur proxy.|  
    |Port|Indique le port du serveur proxy.|  
    |Type|Spécifie le protocole utilisé par le serveur proxy.|  
    |Nom d'utilisateur|Indique le nom d'utilisateur du serveur proxy.|  
    
    **Sécurité**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Accéder à n’importe quel hôte de serveur SSH|Lorsque **True**, le port d’envoi accepte n’importe quelle touche de l’hôte public SSH à partir du serveur. Lorsque **False**, le port correspond à la clé d’hôte avec la clé spécifiée dans le **SSHServerHostKey** propriété.<br /><br /> **Valeur par défaut :** False|  
    |Mode d’authentification client|Spécifie la méthode d’authentification utilisée par le port d’envoi pour authentifier le client sur le serveur SSH. Si la valeur **mot de passe**, vous devez entrer la valeur dans la **mot de passe** propriété. Si la valeur **PublicKeyAuthentication**, vous devez entrer la clé privée de l’utilisateur dans le **PrivateKey** propriété. Si la valeur **MultiFactorAuthentication** vous devez fournir **nom d’utilisateur** avec son **mot de passe** et **PrivateKey**. En outre, si la clé privée est protégée par un mot de passe, entrez le mot de passe ainsi qu’à la **PrivateKeyPassword** propriété.<br /><br /> **Valeur par défaut :** mot de passe|  
    |Chiffrement | Disponible à partir de BizTalk Server 2013 R2.<br/><br/>Entrez le type d’algorithme de chiffrement.<br/><br/>Options de BizTalk Server 2013 R2 : Auto, AES et TripleDES<br/><br/>Options de BizTalk Server 2016 : automatique, AES, Arcfour, Blowfish, TripleDES et DES|  
    |Mot de passe|Spécifiez le mot de passe utilisateur SFTP si vous définissez la **ClientAuthenticationMode** à **mot de passe**.|  
    |Clé privée|Spécifiez la clé privée pour l’utilisateur SFTP si vous définissez la **ClientAuthenticationMode** à **PublicKeyAuthentication**.|  
    |Mot de passe de clé privée|Spécifiez un mot de passe clé privée, si nécessaire, pour la clé spécifiée dans le **PrivateKey** propriété.|  
    |Hôte du serveur SSH empreintes clé|Spécifie l’empreinte digitale du serveur utilisé par l’adaptateur pour authentifier le serveur si la **AccessAnySSHServerHostKey** est définie sur **False**. Si les empreintes ne correspondent pas, la connexion échoue.|  
    |Nom d’utilisateur|Spécifie un nom d’utilisateur pour le serveur FTP sécurisé.|  
    
    **SSH Server**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Ajoutez si existe|Si le fichier transféré vers le serveur FTP sécurisé existe déjà dans la destination, cette propriété spécifie si les données du fichier en cours de transfert doivent être ajoutées au fichier existant. Si la valeur **True**, les données sont ajoutées. Si la valeur **False**, le fichier sur le serveur de destination est remplacé.<br /><br /> **Valeur par défaut :** False|  
    |Chemin d’accès du dossier|Spécifie le chemin d’accès au dossier sur le serveur FTP sécurisé dans lequel le fichier est copié.|  
    |Port|Spécifie l'adresse de port pour le serveur FTP sécurisé sur lequel le transfert de fichiers a lieu.|  
    |Adresse du serveur|Spécifie le nom ou l'adresse IP du serveur FTP sécurisé.|  
    |Nom de fichier cible|Spécifie le nom sous lequel le fichier est transféré vers le serveur FTP sécurisé. Vous pouvez également utiliser des macros pour le nom de fichier cible.|  
  
4.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="use-a-newer-winscp-version"></a>Utilisez une version plus récente de WinSCP

Pour utiliser une version plus récente de WinSCP avec BizTalk Server, ajoutez une redirection d’assembly afin que BizTalk sache quel assembly à charger. La redirection est configurée dans les fichiers de configuration de BizTalk Server : BTSNTSVC.exe.config (instances d’hôte 32 bits) et BTSNTSVC64.exe.config (instances d’hôte 64 bits).

Les éléments suivants inclut des exemples de syntaxe de configuration. Veillez à remplacer `%NEWVERSION%` avec votre version :

```
<configuration>
 <runtime>
  <assemblyBinding>
   <dependentAssembly>
    <assemblyIdentity name="WinSCPnet" publicKeyToken="2271ec4a3c56d0bf" culture="neutral" />
    <bindingRedirect oldVersion="1.2.10.6257" newVersion="%NEWVERSION%"/>
   </dependentAssembly>
  </assemblyBinding>
 </runtime>
</configuration>
```

Lorsque vous avez terminé, votre configuration ressemble à ce qui suit :  

![Redirection d’assembly dans le fichier de configuration.](media/AssemblyRedirect.png)

## <a name="frequently-asked-questions"></a>Forum aux questions  
  
|Question|Réponse|  
|--------------|------------|  
|Quels serveurs SFTP sont pris en charge ?|Consultez [prise en charge des serveurs SFTP](http://social.technet.microsoft.com/wiki/contents/articles/29940.biztalk-serverbiztalk-services-supported-sftp-servers.aspx). À partir de BizTalk Server 2016, l’adaptateur SFTP utilise WinSCP pour se connecter à SFTP. Par conséquent, les serveurs SFTP qui prennent en charge WinSCP doivent fonctionner.|  
|Est-il possible d'utiliser l'adaptateur SFTP avec la méthode d'authentification mutuelle (clé publique et mot de passe) ?|-En commençant par **BizTalk Server 2013 R2**, Oui. Si la valeur **MultiFactorAuthentication** vous devez fournir **nom d’utilisateur** avec son **mot de passe** et **PrivateKey**. En outre, si la clé privée est protégée par un mot de passe, spécifiez le mot de passe ainsi qu’à la **PrivateKeyPassword** propriété.<br /><br /> -Pour **BizTalk Server 2013**, **mot de passe** ou **PublicKeyAuthentication** peut être utilisé. **MultiFactorAuthentication** n’est pas pris en charge dans l’adaptateur SFTP livré avec BizTalk Server 2013.|  
|Quels sont les formats de clé privée pris en charge ? Le format de clé privée OpenSSH peut-il être utilisé ?|L'adaptateur SFTP prend en charge uniquement le format de fichier de clé privée PuTTY. Il est possible d'utiliser PuTTYgen pour effectuer une conversion d'OpenSSH au format .ppk.|  
|Pour SSHServerHostKeyFingerPrint, quels algorithme d'empreintes digitales et format faut-il utiliser ?|Vous devez utiliser l’empreinte MD5 de la clé du serveur dans le format : `ssh-rsa 2048 90:e4:9b:67:d9:22:a7:5f:6f:33:db:6a:b1:23:96:12`.|  
|L'adaptateur SFTP prend-il en charge le chiffrement 256 bits ?|Oui. L'adaptateur SFTP prend en charge le chiffrement 256 bits. Les algorithmes de chiffrement pris en charge sont les suivants :<br /><br /> -Le chiffrement AES : 256 bits, 192 bits ou 128 bits SDCTR ou CBC<br /><br /> -Le chiffrement 3DES (Triple-DES) : 168 bits SDCTR ou CBC|  
|Quelles versions de SSH sont prises en charge par l'adaptateur ?|Uniquement SSH2. Il est impossible d'établir la connexion avec les serveurs SFTP avec la version SSH1.|  
|La casse de masque de fichier importe-t-elle ?|Non. *.txt et \*. TXT fonctionne de la même façon. Installez la dernière mise à jour cumulative pour BizTalk Server 2013. Version de BizTalk Server 2013 RTM avait des masques de fichier respectant la casse.|  
|L'exportation des liaisons génère un champ de mot de passe vide. Lorsque vous tentez de créer un emplacement de réception en important ces liaisons, quelles modifications doivent être effectuées ?|Modifiez le fichier de liaison en modifiant le champ de mot de passe. En outre, dans `<Password vt="1">MySecretPassword</Password>`, **vt = « 1 »** indique une valeur null. Remplacez-la par **vt = « 8 »**, ce qui indique une chaîne. Par exemple :<br /><br /> `<Password vt="8">MySecretPassword</Password>`<br /><br /> Pour plus d’informations, consultez [http://msdn.microsoft.com/library/system.runtime.interopservices.varenum (v=vs.100).aspx](http://msdn.microsoft.com/library/system.runtime.interopservices.varenum\(v=vs.100\).aspx)|  
|Comment spécifier les chemins d'accès au fichier ?|Normalement, les chemins d'accès sont spécifiés au format `/folder/pathname`. Toutefois, différents serveurs requièrent des formats différents, avec ou sans barres obliques de début ou de fin. Par conséquent, vous pouvez également essayer le format suivant :<br /><br /> -                   `/folder/pathname`<br /><br /> -                   `/folder/pathname/`<br /><br /> -                   `folder/pathname`<br /><br /> -                   `folder/pathname/`|  
  

