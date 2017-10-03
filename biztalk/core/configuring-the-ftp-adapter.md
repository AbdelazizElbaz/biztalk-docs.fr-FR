---
title: "Configuration de l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FTP adapters, configuring
- configuring [FTP adapters]
ms.assetid: 7e7d2e2d-142e-4459-be25-efd501b396d2
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 203f6b7ce49dfba26c4883d5b26afee6bcc82f49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-ftp-adapter"></a>Configuration de l'adaptateur FTP


## <a name="before-you-begin"></a>Avant de commencer
- L'adaptateur FTP prend en charge la lecture et l'écriture de données à partir d'un serveur FTP sécurisé. L’adaptateur prend en charge le transfert de fichiers à partir d’un serveur FTP sur SSL Secure Sockets Layer () / niveau de sécurité TLS (Transport). 
- L’adaptateur FTP prend en charge le téléchargement de fichiers à partir des emplacements de fichier en lecture seule. 
- L’adaptateur FTP prend en charge le transfert atomique de fichiers pour le mode ASCII également.

Consultez [meilleures pratiques et recommandations pour l’adaptateur FTP](../core/best-practices-and-recommendations-for-the-ftp-adapter.md).


## <a name="configure-the-receive-location"></a>Configurer l’emplacement de réception

Vous pouvez définir FTP propriétés d’emplacement de l’adaptateur de réception dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies dans l’emplacement de réception, les valeurs du Gestionnaire de réception par défaut dans la console Administration de BizTalk Server sont utilisés.  
  
> [!NOTE]
>  Avant d’exécuter la procédure suivante, vous devez avoir déjà ajouté un port de réception. Consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application dans laquelle vous souhaitez créer un emplacement de réception.  
  
2.  Dans le volet gauche, cliquez sur le **Ports de réception** nœud. Dans le volet droit, cliquez sur le port de réception est associé à un emplacement de réception existant ou que vous souhaitez associer à un nouvel emplacement de réception, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**. Dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau** pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **FTP** dans la liste déroulante et puis cliquez sur **configurer**.  
  
5.  Dans **propriétés du Transport FTP**, procédez comme suit :  

    **Traitement par lots**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre maximal de fichiers**|Indiquer le nombre maximal de fichiers par lot BizTalk Server.<br /><br /> La valeur zéro (0) indique qu'aucune limite n'est définie.<br /><br /> **Valeur par défaut :** 0|  
    |**Taille maximale**|Indiquer le nombre maximal d'octets par lot BizTalk Server.<br /><br /> La valeur zéro (0) indique qu'aucune limite n'est définie.<br /><br /> **Valeur par défaut :** 0|  
    
    **Pare-feu**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|     
    |**Adresse**|Indiquer l'adresse du pare-feu, à savoir un nom DNS ou une adresse IP.|  
    |**Mode**|Indiquez le mode utilisé par l'adaptateur pour se connecter au serveur FTP.<br /><br /> **Valeurs valides :** passif et actif<br /><br /> En mode actif, le serveur FTP se connecte à un port ouvert par l'adaptateur FTP. En mode passif, l'adaptateur FTP se connecte à un port ouvert par le serveur FTP.<br /><br /> **Valeur par défaut :** Active|  
    |**Mot de passe**|Indiquer le mot de passe du pare-feu.|  
    |**Port**|Indiquer le port du pare-feu.<br /><br /> **Valeurs valides :** 1 et 65 535 inclus<br /><br /> **Valeur par défaut :** 21|  
    |**Type**|Indiquer le type de pare-feu déployé.<br /><br /> **Valeurs valides :** aucun, Socks 4 et Socks 5<br /><br /> **Valeur par défaut :** None|  
    |**Utilisateur**|Indiquer le nom d'utilisateur associé au pare-feu.|  
    
    **FTP**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|      
    |**Compte**|Indiquer le nom du compte pour le serveur FTP. Cette option est déconseillée et l’utilisation de cette propriété est déconseillée.|  
    |**Après obtention**|Indiquer les commandes FTP à exécuter après l’obtention du fichier. Séparez les commandes par un point-virgule (;).|  
    |**Avant obtention**|Indiquer les commandes FTP à exécuter avant l’obtention du fichier. Séparez les commandes par un point-virgule (;). **Remarque :** commande QUIT n’est pas prise en charge avant l’obtention du fichier.|  
    |**Seuil d’erreur**|Indiquer le nombre d'erreurs que le serveur BizTalk Server peut rencontrer avant que l'emplacement ne soit désactivé.<br /><br /> **Valeur par défaut :** 10|  
    |**Masque de fichier**|Indiquer le filtre de masque de fichier à utiliser pour la transmission des fichiers. |  
    |**Dossier**|Indiquer l'emplacement d'interrogation sur le serveur FTP.|      
    |**Type de serveur FTP** | Nouveau commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br/><br/>Cette propriété permet de choisir un serveur FTP qui ne requiert pas la commande SYST. Les options sont None, AIX, détecter, GXS, MVS, OS400 et autres. <br/><br/>Si la valeur **aucun**, la commande SYST est utilisée. **Autres** est utilisé lorsque le type de système d’exploitation ne rentre dans aucune des catégories spécifiées. <br /><br /> **Valeur par défaut :** None|    
    |**Journal**|Indiquez l'emplacement d'enregistrement d'une copie du fichier journal. Ce fichier permet de diagnostiquer les conditions d’erreur lors de l’envoi ou réception de fichiers via FTP.|  
    |**Taille max. de fichier**|Indiquer la taille maximale de téléchargement des fichiers (en Mo).<br /><br /> Zéro (0) indique que la taille des fichiers n'est pas limitée.<br /><br /> **Valeur par défaut :** 100|  
    |**Mot de passe**|Indiquer le mot de passe utilisateur pour vous connecter au serveur FTP.|  
    |**Port**|Indiquer l'adresse du port pour ce serveur FTP.<br /><br /> **Valeur par défaut :** 21|  
    |**Représentation sous forme de**|Permet de sélectionner la méthode de réception des données via FTP.<br /><br /> **Valeurs valides :** binaire ou ASCII<br /><br /> **Valeur par défaut :** binaire|  
    |**Server**|Indiquer le nom de serveur ou l'adresse IP du serveur FTP. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Application associée SSO**|Indiquer l'application associée à authentification unique de l'entreprise.|  
    |**Utilisez la liste des noms (NLST)**|Indiquer la méthode utilisée par l'adaptateur pour répertorier les fichiers. Pour afficher les noms de fichier au lieu de la liste de fichiers définie par le système, définissez cette valeur sur Oui.<br /><br /> **Valeur par défaut :** N°|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur pour la connexion au serveur FTP.|  
    
    **Interrogation**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|         
    |**Supprimer après téléchargement**|Indiquer si l'adaptateur supprime un fichier du serveur FTP après l'avoir téléchargé.<br /><br /> **Valeur par défaut :** Oui **Remarque :**|  
    |**Activer la comparaison d’horodatage**|Indiquer si l'adaptateur télécharge de nouveau un fichier selon le cachet de date modifié. Lorsque l'adaptateur ne possède pas d'autorisations de suppression sur le serveur FTP, la commande MDTM (heure de modification) permet à l'adaptateur de savoir si un fichier a été modifié depuis le dernier téléchargement.  Selon la valeur de cette propriété, le fichier est de nouveau téléchargé.<br /><br /> **Valeur par défaut :** non **Remarque**: dans le cas où le serveur FTP ne prend pas en charge MDTM, définissez le **intervalle de retéléchargement** propriété. **Remarque :** cette propriété est applicable uniquement lorsque **supprimer après téléchargement** est définie sur non.|  
    |**Intervalle**|Indiquer la fréquence d'interrogation de cet emplacement. Pour effectuer une interrogation continue, définissez cette valeur sur zéro (0).<br /><br /> **Valeur par défaut :** 60|  
    |**Intervalle de retéléchargement**|Spécifiez l’intervalle après lequel l’adaptateur télécharge à nouveau. Cette propriété est applicable uniquement lorsque les deux **supprimer après téléchargement** et **activer d’horodatage** sont définies sur non.<br /><br /> **Valeur par défaut :** -1<br /><br /> -1 indique que l'adaptateur téléchargera de nouveau les fichiers.<br /><br /> 0 indique que l'adaptateur téléchargera le fichier à chaque cycle d'interrogation.|  
    |**Unité**|Spécifiez le type d’unités pour la **intervalle** et **intervalle de retéléchargement** propriétés.<br /><br /> **Valeurs valides :** secondes, Minutes, heures et jours<br /><br /> **Valeur par défaut :** secondes|  
    
    **SSL**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|
    |**Hachage du certificat client**|Spécifier le code de hachage SHA1 du certificat client qui doit être utilisé dans la négociation SSL.<br /><br /> Selon ce hachage, le certificat client est récupéré dans le magasin personnel du compte d'utilisateur sous lequel l'instance de l'hôte de BizTalk est exécutée.|  
    |**Mode de connexion FTPS**|Spécifier le mode de connexion SSL au serveur FTPS.<br /><br /> **Valeurs valides :** implicite ou explicite<br /><br /> **Valeur par défaut :** explicite|  
    |**Utilisez la Protection des données**|Définir ce paramètre sur Oui si l'adaptateur doit utiliser le chiffrement SSL lors de l'envoi et de la réception des fichiers de données à partir du serveur FTPS. Définissez ce paramètre sur Non pour que l'adaptateur envoie et réceptionne les fichiers de données en texte brut. **Remarque :** cette propriété s’applique uniquement si le **utiliser SSL** est définie sur Oui. <br /><br /> **Valeurs valides :** Yes ou No<br /><br /> **Valeur par défaut :** Oui|  
    |**Utiliser SSL**|Indiquer si l'adaptateur FTP doit utiliser une connexion SSL pour communiquer avec le serveur FTPS.<br /><br /> **Valeurs valides :** Yes ou No<br /><br /> **Valeur par défaut :** N°|  
    
    **Paramètres de réglage**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|     
    |**Délai d’expiration des données de réception**|Indiquer le délai (en millisecondes) avant l'abandon de l'appel de réception. Cette propriété vous permet d’empêcher un serveur lent à partir de l’emplacement de réception cesse de répondre.<br /><br /> **Valeur par défaut :** 90000|  
    |**Dossier temporaire**|Indiquer l'emplacement du dossier temporaire. Cet emplacement permet la récupération après un échec de transfert.|  
  
6.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
> [!NOTE]
>  Ne configurez pas plusieurs emplacements de réception FTP pour interroger la même URL FTP. Si plusieurs emplacements de réception FTP interrogent la même URL simultanément, chaque emplacement de réception peut recevoir une copie du fichier, ce qui peut entraîner des données dupliquées. Ce comportement survient car le protocole FTP n'a pas été configuré pour le verrouillage des fichiers lors de leur lecture à partir de l'URL cible.  
>   
>  Pour fournir une haute disponibilité pour le protocole FTP l’adaptateur de réception, vous devez configurer l’adaptateur de réception FTP à exécuter dans une instance d’hôte BizTalk en cluster. Consultez [considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  

## <a name="configure-the-send-port"></a>Configurer le port d’envoi

Vous pouvez définir les propriétés de l’adaptateur FTP send port dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour le port d’envoi, la valeur par défaut le servent de valeurs dans la console Administration de BizTalk Server de gestionnaire d’envoi.  
  
1.  Dans la console Administration de BizTalk Server, créez un port d’envoi ou double-cliquez sur un port d’envoi existant pour le modifier. Consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurer toutes les options de port d’envoi, puis, dans le **Transport** section de la **général** , spécifiez **FTP** pour le **Type** option.  
  
2.  Sur le **général** page, dans le **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans **propriétés du Transport FTP**, procédez comme suit :  
  
    **Pare-feu**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|    
    |**Adresse**|Indiquer l'adresse du pare-feu, à savoir un nom DNS ou une adresse IP.|  
    |**Mode**|Spécifier le mode utilisé par l'adaptateur pour se connecter au serveur FTP.<br /><br /> **Valeurs valides :** passif et actif<br /><br /> En mode actif, le serveur FTP se connecte à un port ouvert par l'adaptateur FTP. En mode passif, l'adaptateur FTP se connecte à un port ouvert par le serveur FTP.<br /><br /> **Valeur par défaut :** Active|  
    |**Mot de passe**|Indiquer le mot de passe du pare-feu.|  
    |**Port**|Indiquer le port du pare-feu.<br /><br /> **Valeurs valides :** entre 1 et 65535 (inclus)<br /><br /> **Valeur par défaut :** 21|  
    |**Type**|Sélectionner le type de pare-feu déployé.<br /><br /> **Valeurs valides :** Socks 4, Socks 5, aucun<br /><br /> **Valeur par défaut :** None|  
    |**Utilisateur**|Indiquer le nom d'utilisateur associé au pare-feu.|  
    
    **FTP**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------| 
    |**Compte**|Ce paramètre est facultatif. Indiquer le nom du compte pour le serveur FTP. L'option est supprimée et l'utilisation de cette propriété est déconseillée.|  
    |**Après placement**|Indiquer les commandes FTP à exécuter après le fichier PUT. Séparez les commandes par un point-virgule (;).|  
    |**Allouer du stockage**|Indiquer si de l'espace de stockage doit être alloué pour les systèmes hôtes existants. Cette option est fournie à des fins de compatibilité descendante.<br /><br /> **Valeurs valides :** non et Oui<br /><br /> **Valeur par défaut :** N°|  
    |**Avant placement**|Indiquer les commandes FTP à exécuter avant le placement du fichier, telles que les commandes permettant de modifier les valeurs par défaut sur le serveur FTP. Séparez les commandes par un point-virgule (;). Aucune commande Ouvrir n'est requise. **Remarque :** commande QUIT n’est pas prise en charge avant le placement du fichier.|  
    |**Dossier**|Indiquer l'emplacement vers lequel déplacer les fichiers sur le serveur FTP.|      
    |**Type de serveur FTP** | Nouveau commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br/><br/>Cette propriété permet de choisir un serveur FTP qui ne requiert pas la commande SYST. Les options sont None, AIX, détecter, GXS, MVS, OS400 et autres. <br/><br/>Si la valeur **aucun**, la commande SYST est utilisée. **Autres** est utilisé lorsque le type de système d’exploitation ne rentre dans aucune des catégories spécifiées. <br /><br /> **Valeur par défaut :** None|  
    |**Journal**|Indiquer l'emplacement où enregistrer une copie d'un fichier journal. Ce fichier permet de diagnostiquer les conditions d'erreur lors de l'envoi ou de la réception de fichiers via l'adaptateur FTP.|  
    |**Mot de passe**|Spécifier le mot de passe de connexion au serveur FTP.|  
    |**Port**|Spécifier l'adresse du port du serveur FTP.<br /><br /> **Valeur par défaut :** 21|  
    |**Représentation sous forme de**|Sélectionner la méthode utilisée par l'adaptateur FTP pour l'envoi de données (au format binaire ou ASCII).<br /><br /> **Valeurs valides :** binaire ou ASCII<br /><br /> **Valeur par défaut :** binaire|  
    |**Server**|Indiquer le nom de serveur ou l'adresse IP du serveur FTP.|  
    |**Application associée SSO**|Indiquer l'application associée à authentification unique de l'entreprise.|  
    |**Nom de fichier cible**|Indiquer un autre nom pour le fichier. Conserver le nom par défaut garantit l'unicité des noms de message pour chaque message envoyé.<br /><br /> **Valeur par défaut :** %MessageID%.xml|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur pour la connexion au serveur FTP.|  
    
    **SSL**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|
    |**Hachage du certificat client**|Spécifier le code de hachage SHA1 du certificat client qui doit être utilisé dans la négociation SSL.<br /><br /> Selon ce hachage, le certificat client est récupéré dans le magasin personnel du compte d'utilisateur sous lequel l'instance de l'hôte de BizTalk est exécutée.|  
    |**Mode de connexion FTPS**|Spécifier le mode de connexion SSL au serveur FTPS.<br /><br /> **Valeurs valides :** implicite ou explicite<br /><br /> **Valeur par défaut :** explicite|  
    |**Utilisez la Protection des données**|Définir ce paramètre sur Oui si l'adaptateur doit utiliser le chiffrement SSL lors de l'envoi et de la réception des fichiers de données à partir du serveur FTPS. Définissez ce paramètre sur Non pour que l'adaptateur envoie et réceptionne les fichiers de données en texte brut. **Remarque :** cette propriété s’applique uniquement si le **utiliser SSL** est définie sur Oui. <br /><br /> **Valeurs valides :** Yes ou No<br /><br /> **Valeur par défaut :** Oui|  
    |**Utiliser SSL**|Indiquer si l'adaptateur FTP doit utiliser une connexion SSL pour communiquer avec le serveur FTPS.<br /><br /> **Valeurs valides :** Yes ou No<br /><br /> **Valeur par défaut :** N°|  
    
    **Paramètres de réglage**
    
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------| 
    |**Nombre maximal de connexions**|Spécifier un nombre maximal de connexions FTP simultanées pouvant être établies vers le serveur. La valeur 0 indique une absence de limite.<br /><br /> **Valeur par défaut :** 0 **Remarque :** cette propriété remplace l’entrée de Registre qui a été utilisée dans les versions antérieures de BizTalk Server pour contrôler la limite de connexion. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ignore l’entrée de Registre utilisée pour contrôler la limite de connexion.|  
    |**Dossier temporaire**|Indiquer l'emplacement d'un dossier temporaire sur le serveur FTP. Ce fichier est d'abord téléchargé ici, puis déplacé vers le dossier FTP de destination. En cas d'échec du transfert, l'adaptateur redémarre le téléchargement du fichier en mode de transfert ASCII et reprend le mode binaire pour le transfert. **Remarque :** si le transfert de fichiers est atomique entre l’emplacement temporaire et l’emplacement approprié sur le serveur FTP, le téléchargement du fichier est également atomique.|  
  
4.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.   


## <a name="ftp-commands-required-by-the-ftp-adapter"></a>Commandes FTP requises par l’adaptateur FTP  
L'adaptateur FTP est soumis aux limitations du protocole FTP. Il requiert que certaines commandes FTP soient disponibles sur le serveur FTP source et de destination.  

L’adaptateur FTP opère comme un client FTP et peut-être nécessiter que les commandes suivantes sont disponibles sur le serveur FTP pour fonctionner correctement : 
 
|Command  |Requis par réception  |Requis par envoi  |
|---------|---------|---------|
|SYST | ✔ <br/><br/>Facultatif en commençant par[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] | ✔<br/><br/>Facultatif en commençant par[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] |
| MAGASIN | |✔|
| RETR | ✔ | |
| Utilisateur |✔ | ✔ |
| PASS | ✔ | ✔ |
| CWD |✔ | ✔ |
| QUIT |✔ | ✔ |
| PORT | ✔ | ✔ |
| PASV | ✔ | ✔ |
| ABOR | ✔ | ✔ |
| TYPE | ✔ | ✔ |
| RNFR | ✔ | ✔ |
| RNTO | ✔ | ✔ |
| DELE | ✔ | ✔ | 
| PWD | ✔ | ✔ |
| LIST | ✔ | ✔ |
| NLST | ✔ | ✔ |
| NOOP | ✔ | ✔ |
| APPE |  | ✔ |
| ALLO | ✔ | ✔ |
| MDTM | ✔ | |
| AUTH TLS | ✔ | ✔ | 
| PBSZ | ✔ | ✔ | 
| PROT | ✔ | ✔ |

 Pour plus d’informations sur ces commandes FTP, consultez :  
  
-   [RFC 959 - File Transfer Protocol](http://go.microsoft.com/fwlink/p/?LinkId=119603) (http://go.microsoft.com/fwlink/p/?LinkId=119603)  
  
-   [RFC 4217 - Securing FTP with TLS](http://go.microsoft.com/fwlink/p/?LinkId=183154) (http://go.microsoft.com/fwlink/p/?LinkId=183154)  
  
-   [RFC 3659 - Extensions to FTP](http://go.microsoft.com/fwlink/p/?LinkId=183155) (http://go.microsoft.com/fwlink/p/?LinkId=183155)  
  
## <a name="configuring-an-ftp-adapter-to-work-with-legacy-hosts"></a>Configuration d’un adaptateur FTP pour travailler avec des hôtes hérités

Cette section traite de ce que vous devez savoir pour faciliter la communication entre l’adaptateur FTP et un macroordinateur.   
> [!NOTE]
>  Vous ne pouvez pas utiliser la fonction de dossier temporaire dans le cadre de l'envoi de fichiers à un hôte MVS ou AS400. La saisie dans ce champ n'est pas prise en charge et génère des erreurs.  
  
> [!IMPORTANT]
>  Les informations suivantes sont des indications et ne doivent pas remplacer celles disponibles dans la documentation AS400 ou IBM.  
  
## <a name="mvs"></a>MVS  
 Pour envoyer des fichiers à un serveur FTP sur un macroordinateur, ce dernier doit prendre en charge le groupe GDG (Generation Data Group) IBM. Dans le champ de nom, chaque nom de fichier ajoute un (+1) au nom du fichier de destination (chemin d'accès complet entouré de guillemets).  
  
## <a name="as400"></a>AS400  
 Il existe trois méthodes pour nommer les fichiers et définir leurs chemins d'accès dans le cadre du transfert de fichiers via un système AS400 :  
  
-   **Champ de nom de fichier**: lors de l’envoi d’un fichier à un serveur FTP, entrez le nom de fichier dans le **nom de fichier** champ. Celui-ci doit être conforme aux conventions d'affectation de noms de fichier du système AS400 car il sera stocké dans le système de fichiers bibliothèque.  
  
-   **Commande quote**: la commande Quote permet d’exécuter un script sur l’ordinateur distant. Entrez la commande Quote dans les **avant d’obtenir**, **avant de placer**, **après**, et **après placement** champs sur un point de terminaison. en utilisant le format suivant :  
  
    ```  
    QUOTE RCMD <command to be run on the remote system>.  
    ```  
  
-   **Intégré du système de fichiers (IFS)**: IFS est une zone sur le système AS400 qui permet le stockage de fichiers basés sur des PC et donc les mêmes conventions d’affectation de noms comme un PC. Pour utiliser le système IFS plutôt que le système de fichiers bibliothèque, vous devez entrer `quote site namefmt 1` comme première commande. Celle-ci indique au système AS400 d'utiliser la convention d'affectation de noms du système IFS.    

   
## <a name="more-good-stuff"></a>Autre contenu intéressant
  
[Propriétés et schéma de propriété de l’adaptateur FTP](../core/ftp-adapter-property-schema-and-properties.md)  

[Meilleures pratiques et recommandations pour l’adaptateur FTP](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[Adaptateur FTP](../core/ftp-adapter.md)