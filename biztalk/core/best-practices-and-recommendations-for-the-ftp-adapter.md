---
title: "Meilleures pratiques et recommandations pour l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, FTP adapters
- FTP adapters, best practices
ms.assetid: f73b2016-d48c-48d8-9ba0-96e26b694d1e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85967756089be91939bf5b6f73b12d36ed8caa51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-and-recommendations-for-the-ftp-adapter"></a>Meilleures pratiques et recommandations pour l’adaptateur FTP
Découvrez les meilleures pratiques, les recommandations de sécurité et les améliorations de l’adaptateur FTP.

## <a name="best-practices"></a>Meilleures pratiques  
  
-   Supprimez régulièrement les fichiers partiellement reçus du dossier temporaire pour éviter que ceux-ci n'utilisent des ressources de l'ordinateur et n'interrompent le service.  
  
-   Lorsque vous utilisez un serveur de diffusion en continu, n'octroyez pas l'accès en lecture au nouveau fichier tant que la base de données MessageBox n'a pas reçu le fichier entier. Si un fichier partiel est envoyé à la base de données MessageBox par l'adaptateur FTP, celle-ci stocke le message, mais l'adaptateur FTP ne peut pas supprimer le message partiel de l'emplacement de réception.  
  
-   Pour assurer la haute disponibilité du gestionnaire de réception de l'adaptateur FTP, celui-ci doit être configuré afin d'être exécuté dans une instance d'hôte BizTalk mise en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  

## <a name="security-recommendations-and-tips"></a>Conseils et des recommandations de sécurité

BizTalk Server peut recevoir des fichiers à partir d’un serveur de transfert de protocole FTP (File) et envoyer des fichiers à un serveur FTP pour d’autres applications. BizTalk Server n'agit pas en tant que serveur FTP.  
  
 FTP est, par nature, non sécurisé : le nom d’utilisateur, mot de passe et autres informations d’identification de parcourent le réseau en texte clair. De même, les fichiers téléchargés sont transférés en texte clair. Il est donc facile de les afficher ou de les falsifier pendant leur transfert. En outre, une attaque de serveur non autorisé peut usurper l'identité du serveur FTP. Dans ce cas, il est difficile de savoir si un serveur FTP spécifique est bien l'ordinateur avec lequel vous tentez de communiquer.  
  
 Pour résoudre ces problèmes, l’adaptateur FTP prend en charge le protocole SSL/TLS qui garantit la confidentialité des données via le chiffrement.  
  
 Pour des considérations générales de sécurité lorsque vous utilisez le protocole FTP, consultez la [Internet FAQ Archives](http://go.microsoft.com/fwlink/p/?LinkId=24779) (http://go.microsoft.com/fwlink/p/?LinkId=24779).   
  
 Il est recommandé d'utiliser les informations suivantes pour la sécurisation et le déploiement de l'adaptateur FTP dans votre environnement :  

- Sécuriser votre serveur et limiter l’accès aux données. Le protocole FTP est vulnérable étant donné qu'il s'agit d'un protocole non sécurisé. Cependant, vous pouvez garantir la sécurité du serveur FTP en utilisant une connexion dédiée et en limitant le serveur et la connexion entre le serveur BizTalk Server et l'hôte FTP. Vous pouvez également définir les stratégies de sécurité du serveur FTP de manière à autoriser les connexions sécurisées avec le client FTP.  

- Configurez l'adaptateur FTP afin qu'il utilise le protocole SSL (Secure Sockets Layer) pour les communications entre l'adaptateur et le serveur FTP. Le protocole SSL garantit la confidentialité des données au moyen d'un chiffrement. Cela signifie donc que l'ID utilisateur et le mot de passe sont chiffrés et qu'ils ne sont pas envoyés en tant que texte brut. L'adaptateur FTP vous permet aussi de chiffrer le canal des données de la connexion FTP. Consultez **améliorations** (dans cette rubrique).
  
-   Pour obtenir le transfert de fichiers sécurisé, configurez les propriétés spécifiques de SSL fournies par l’adaptateur FTP. Consultez **améliorations** (dans cette rubrique). 
  
-   L’adaptateur FTP prend en charge des demandes FTP pour les commentaires (RFC) 959. Consultez le [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?LinkId=24781) (http://go.microsoft.com/fwlink/p/?LinkId=24781). L'adaptateur FTP ne prend pas en charge le protocole FTP sécurisé (SFTP). Consultez le [adaptateur SFTP](../core/sftp-adapter.md).
  
-   Vous pouvez utiliser l'adaptateur FTP sur plusieurs pare-feu. Selon le type de pare-feu utilisé, vous devrez peut-être configurer un ou plusieurs des propriétés de pare-feu suivantes : nom d’utilisateur, mot de passe, ordinateur, port, type de pare-feu (aucun, socks 4, socks 5) et le mode.  
  
-   Nous vous recommandons de que vous placez le serveur FTP distant dans un emplacement sécurisé. Pour réduire le nombre des attaques de serveur non autorisé, vous devez garantir la sécurité physique et réseau de ce serveur.  
  
-   L'adaptateur FTP prend en charge l'utilisation de l'authentification unique (SSO) de l'entreprise. Consultez [implémentation Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md).  
  
-   Par défaut, l'adaptateur de réception FTP doit disposer d'autorisations en écriture sur le serveur FTP car il supprime des fichiers du serveur une fois ceux-ci téléchargés. Toutefois, l’adaptateur FTP prend en charge le téléchargement de fichiers à partir d’emplacements en lecture seule. Consultez **améliorations** (dans cette rubrique).
  
- Lorsque vous utilisez un port d'envoi FTP, vous devez spécifier et stocker une combinaison formée d'un ID utilisateur et d'un mot de passe au moment de la configuration du port d'envoi. L'adaptateur exploite ces informations pour se connecter au serveur FTP. Les informations d'identification de l'utilisateur sont stockées en tant que texte brut dans une base de données SQL Server. Dans le cas d'un port d'envoi dynamique, ces informations sont envoyées au serveur FTP. Si les exigences d'un environnement de production supposent une sécurité optimale, préférez l'envoi d'informations d'identification anonymes au serveur.  
  
-   Lorsque le système vous invite à entrer un compte, nous vous recommandons d’entrer un compte d’utilisateur et non le compte système local. Cela vous permet de mettre en place une sécurité accrue, mais cela permet aussi à l'adaptateur d'être exécuté en mode automatique, lequel ne requiert pas d'opération d'ouverture de session.  

## <a name="enhancements"></a>Améliorations

### <a name="transferring-data-to-and-from-a-secure-ftp-server"></a>Transfert de données vers et depuis un serveur FTP sécurisé  
 L’adaptateur FTP prend en charge les transferts de fichiers à partir d’un serveur FTPS via SSL Secure Sockets Layer () / niveau de sécurité TLS (Transport). Le protocole SSL/TLS garantit la confidentialité des données grâce au chiffrement. Vous devez activer le mode sécurisé en configurant les propriétés spécifiques de SSL fournies par l'adaptateur. Comme l'adaptateur permet de lire et d'écrire des données depuis un serveur FTP sécurisé, les propriétés spécifiques de SSL sont disponibles lors de la configuration des gestionnaires/ports d'envoi, ainsi qu'avec les gestionnaires/emplacements de réception.  

En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], l’adaptateur FTP ne requiert plus la commande SYST : 

- **Type de serveur FTP** property – définissez cette propriété pour utiliser un serveur qui ne nécessite pas la commande SYST.
   
 Les options suivantes sont disponibles pour configurer les propriétés spécifiques de SSL :  

-   **Utiliser SSL** property – définissez cette propriété afin que l’adaptateur FTP doit utiliser SSL pour chaque session de transfert.  
  
-   **Activer la Protection des données** property – définissez cette propriété pour activer le chiffrement de données. Les stratégies de sécurité du serveur FTPS doivent être compatibles avec les connexions SSL sécurisées avec l'adaptateur afin que ce paramétrage fonctionne.  
  
-   **Mode de connexion FTPS** property – définissez cette propriété pour déterminer quand la sécurité est activée :  
  
    -   Dans **implicite** , mode de sécurité est automatiquement activée dès que l’adaptateur se connecte au serveur.  
  
    -   Dans **Explicit** mode, l’adaptateur envoie une commande pour établir un canal de contrôle sécurisé.  
  
> [!NOTE]
>  L'adaptateur FTP ne prend pas en charge les vérifications de révocation sur les certificats de serveur.  
  
### <a name="support-for-downloading-files-from-locations-marked-as-read-only"></a>Prise en charge du téléchargement de fichiers à partir d'emplacements marqués en lecture seule  
L’adaptateur FTP prend en charge le téléchargement de fichiers à partir d’emplacements de fichiers en lecture seule. L'adaptateur maintient à présent une liste des fichiers téléchargés dans une base de données. Lors du téléchargement suivant, la liste des fichiers sur le serveur FTP est comparée à la liste des fichiers maintenue, et seuls les nouveaux fichiers sur le serveur sont téléchargés. Pour prendre en charge les scénarios où un fichier existant est mis à jour entre deux téléchargements, vous pouvez configurer l’adaptateur pour vérifier l’horodatage des fichiers en définissant le **activer d’horodatage** emplacement de réception de propriété pour le protocole FTP. Dans ce cas, même si le nom de fichier est identique, mais l’horodatage est mis à jour, l’adaptateur télécharge le fichier.  
  
 Parfois, le serveur FTP ne prend pas en charge l'association d'un cachet de date modifié à un fichier. L'adaptateur vous permet alors de spécifier un intervalle après lequel le fichier est retéléchargé. Vous configurez cet intervalle en définissant le **intervalle de retéléchargement** emplacement de réception de propriété pour le protocole FTP.  
  
 Le tableau suivant répertorie le comportement attendu de l’adaptateur FTP pour différentes valeurs définies pour le **supprimer après téléchargement**, **activer d’horodatage** et **intervalle de retéléchargement** propriétés.  
  
|Supprimer après téléchargement|Activer la comparaison de cachets de date|Intervalle de retéléchargement|Comportement de l'adaptateur|  
|---|---|---|---|  
|Oui|Non applicable|Non applicable|L'adaptateur supprime un fichier du serveur FTP après l'avoir téléchargé. Il s'agit du comportement par défaut de l'adaptateur.|  
|Non|Oui|Non applicable|L'adaptateur ne supprime pas le fichier du serveur FTP après l'avoir téléchargé. Au lieu de cela, il compare la date de dernière modification du fichier à l'aide de la commande MDTM. En fonction de l'horodatage, l'adaptateur télécharge le fichier à nouveau.|  
|Non|Non|Applicable|L'adaptateur FTP télécharge un fichier du serveur FTP après l'intervalle que vous spécifiez, que le fichier ait été modifié ou non.|  
  
### <a name="support-for-atomic-file-transfer-in-ascii-mode"></a>Prise en charge du transfert atomique de fichiers en mode ASCII  
 L’adaptateur FTP prend en charge le transfert atomique de fichiers pour le mode ASCII. Pour activer le transfert atomique de fichiers pour le mode ASCII, l’adaptateur utilise le **dossier temporaire** propriété. Cette propriété définit un emplacement temporaire sur le serveur FTP vers lequel le fichier est tout d'abord déplacé. Une fois que le fichier est complètement transféré vers l'emplacement temporaire, le fichier est ensuite déplacé vers l'emplacement pertinent sur le serveur FTP. Ici, on part du principe que le transfert de fichiers est atomique entre l'emplacement temporaire et l'emplacement pertinent sur le serveur FTP.  
  
> [!NOTE]
>  L’extension de l’utilisation du dossier temporaire à un fichier ASCII est applicable uniquement pour le **envoyer**et ne s’applique pas aux **réception**. La principale raison de l’implémentation de cette fonctionnalité réside dans le fait qu’une application tierce ne lit pas un fichier tant que ce dernier n’a pas été complètement écrit. Dans le cas où BizTalk reçoit le fichier, l’adaptateur envoie le fichier à BizTalk uniquement après sa lecture complète.  
  
> [!NOTE]
>  En mode binaire, le **dossier temporaire** propriété peut également être utilisée pour reprendre le transfert de fichiers s’il existe entre une défaillance. Cela ne s'applique pas au mode ASCII. Pour le mode ASCII, la **dossier temporaire** propriété est utilisée uniquement pour le transfert atomique de fichiers.  
  
 
## <a name="next"></a>Suivant 
[Configuration de l’adaptateur FTP](../core/configuring-the-ftp-adapter.md)  

## <a name="see-also"></a>Voir aussi  
 [Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)
