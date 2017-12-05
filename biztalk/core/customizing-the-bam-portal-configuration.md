---
title: Personnalisation de la Configuration du portail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 507bd5f0-b2a0-4d52-85f8-9d984138ca79
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd99c0746c09f88d71e3a44e625ae5c52458f2f3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="customizing-the-bam-portal-configuration"></a>Personnalisation de la configuration du portail BAM
Il est possible de configurer de nombreuses options dans le portail BAM. Les procédures suivantes décrivent la manière de modifier le portail BAM pour obtenir les meilleures conditions d'utilisation possibles.  
  
> [!NOTE]
>  Lorsque vous configurez le portail en tant qu'utilisateur non-administrateur empruntant une identité, il est possible que vous deviez vous déconnecter, puis vous reconnecter pour avoir accès aux composants de portail BAM sans avoir à entrer des informations d'identification. Observez par exemple le scénario suivant :  
>   
>  Vous configurez le service Web ou le portail BAM avec un utilisateur non-administrateur empruntant une identité. Vous définissez ensuite des permissions de sorte que le groupe Tout le monde n'ait pas accès au portail. Vous créez un groupe local nommé PortalUsersGroup et affectez ce groupe en tant que groupe Utilisateurs du portail. Cela signifie que seuls les utilisateurs de ce groupe ont accès au portail. Une fois que vous avez configuré le portail BAM, ajoutez l'utilisateur en cours au groupe Utilisateurs du portail. Lorsque vous ouvrez le portail BAM, vous êtes invité à entrer vos informations d'identification. En revanche, si vous vous déconnectez et que vous vous reconnectez immédiatement, vous pouvez ouvrir le portail BAM sans être obligé d'entrer à nouveau vos informations d'identification.  
>   
>  BizTalk Server prend en charge les comptes d'utilisateur et de groupe locaux uniquement dans des configurations ne comprenant qu'un seul ordinateur. BizTalk Server prend en charge les comptes d'utilisateur et de groupe de domaine dans des configurations comprenant un ou plusieurs ordinateurs.  
  
## <a name="running-the-bam-portal-in-a-64-bit-environment"></a>Exécution du portail BAM dans un environnement 64 bits  
 Si vous utilisez Internet Information Services (IIS) dans un environnement 64 bits, vous devez configurer IIS en mode 32 bits pour exécuter le portail BAM. 
  
> [!IMPORTANT]
>  Il n'est pas utile de configurer IIS 7 en mode 32 bits.  
  
#### <a name="to-set-a-64-bit-mode-iis-installation-to-32-bit-mode"></a>Pour définir en mode 32 bits des services Internet initialement installés en mode 64 bits  
  
1.  Ouvrez une invite de commandes et exécutez le **adsutil** commande. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Tapez la commande suivante à l’invite de commandes : `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`.  
  
3.  Fermez l'invite de commande.  
  
## <a name="configuring-the-bam-portal-banner"></a>Configuration de la bannière du portail BAM  
 Vous pouvez modifier la page du portail BAM de sorte qu'elle affiche des éléments textuels et graphiques similaires en les adaptant à votre entreprise :  
  
-   le logo Windows Server System, situé dans l'angle supérieur droit de la page de portail BAM :  
  
 Dans la procédure suivante, il s'agit de modifier un fichier de feuille de style (.css) en cascade pour personnaliser l'apparence du portail BAM. Les modifications apportées aux classes spécifiées sont les seules à être prises en charge. Autant que possible, l'impact des modifications sur les classes a été isolé afin que les erreurs générées au cours du processus de modification n'empêchent pas le portail BAM de fonctionner.  
  
> [!CAUTION]
>  La modification d'autres classes du fichier de styles CSS styles.css entraîne le masquage des données et des composants de portail, ce qui peut rendre le portail inutilisable.  
  
#### <a name="to-configure-the-banner"></a>Pour configurer la bannière  
  
1.  Modifiez le fichier Web.config du portail BAM. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis cliquez sur **OK**.  
  
2.  Le contenu principal de démarrage rapide est remplaçable en modifiant la ligne suivante : \<Ajouter clé = « MainPageContentUrl » value="~/MainPageContent.htm"/\>. Modification **MainPageContent.htm** dans le champ de valeur pour pointer vers votre propre fichier HTML. Ce fichier doit appartenir au même répertoire que le fichier Web.config.  
  
3.  Modifiez la page de texte d’identification en ajoutant la ligne suivante au fichier web.config : \<Ajouter clé = « PortalTitle » value = « New Identifying text » /\>. Insérez le texte permettant d'identifier le portail dans le champ de valeur approprié.  
  
4.  Modifiez le fichier styles.css portail BAM. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\styles.CSS, puis cliquez sur **OK**.  
  
5.  Modifier le logo dans le coin supérieur droit en recherchant la classe .headerLogo div et en modifiant la ligne suivante : image d’arrière-plan : url(".. / images/WSS_Logo.gif ») ; pour pointer vers le fichier image que vous avez créé. Nous vous recommandons d'utiliser une image de format .gif.  
  
6.  Modifiez l’icône SharePoint en recherchant la classe .headerPageIcon div et en modifiant la ligne suivante : image d’arrière-plan : url(".. / images/btsSuiteProduction.gif ») ; pour pointer vers le fichier image que vous avez créé.  
  
7.  Enregistrez le fichier.  
  
8.  Ouvrez le portail BAM pour visualiser vos modifications.  
  
## <a name="modifying-the-bam-portal-webconfig-file"></a>Modification du fichier web.config dans le portail BAM  
 Si votre portail BAM réside sur un serveur utilisant les certificats d'authentification unique de l'entreprise pour SSL (Secure Sockets Layer), vous devez configurer le portail de manière à ce qu'il accepte l'URL appropriée au certificat.  
  
#### <a name="to-modify-the-bam-portal-to-support-ssl-sites"></a>Pour paramétrer le portail BAM afin qu'il prenne en charge les sites SSL  
  
1.  Ouvrez le fichier web.config à l'aide du Bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis cliquez sur **OK**.  
  
2.  Modifiez les deux lignes suivantes dans le fichier pointant vers l'emplacement de votre portail SSL :  
  
    ```  
    <add key="BamQueryWSUrl" value="http://localhost/BAM/BamQueryService/BamQueryService.asmx"/>  
    <add key="BamManagementWSUrl" value="http://localhost/BAM/BamManagementService/BamManagementService.asmx"/>  
    ```  
  
3.  Enregistrez le fichier.  
  
 Le portail BAM affiche et accepte les données dans le format pris en charge par la culture dans laquelle il a été configuré. Cette configuration se fait dans le fichier Web.config. Le portail web ignore les informations de l'en-tête « Accept-Language » envoyées par Internet Explorer. Par exemple, supposons que vous exécutez Internet Explorer, qui est définie pour un paramètre de culture japonaise et avez configuré le portail BAM pour utiliser des États-Unis. Paramètre de culture anglais. Dans ce cas des éléments de données, tels que les dates et les nombres entiers seront affichés, acceptés et triés selon les règles pour les États-Unis Paramètre de culture anglais plutôt que les règles appropriées pour le paramètre de culture japonaise. Toutes les informations spécifiques à la culture entrées à l’aide de la mise en forme japonaise seront considérée comme invalide par le portail BAM, car il s’attend à recevoir des données mises en forme pour les États-Unis Anglais.  
  
 Pour parvenir à une certaine cohérence entre la gestion de l'affichage et le formatage des données dépendant des paramètres culturels, optez pour une langue qui convienne à tous les clients du portail BAM. Configurez le portail BAM avec cette culture. Vous devez vérifier que les paramètres culturels sont les mêmes pour tous les clients en installant le pack d'interface utilisateur multilingue.  
  
 Non-US Les installations en anglais de l’analyse BAM il peut être nécessaire définir le paramètre de culture dans le fichier web.config. Voici une liste des cas où ce paramétrage doit être effectué :  
  
-   Pour localiser le format d'affichage de la date et de l'heure  
  
-   Pour localiser le format d'affichage de la devise  
  
#### <a name="to-modify-the-culture-setting-of-the-portal"></a>Pour modifier le paramétrage de la culture dans le portail  
  
1.  Ouvrez le fichier web.config à l'aide du Bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis cliquez sur **OK**.  
  
2.  Modifiez les attributs de culture dans la ligne suivante dans le fichier afin de refléter les paramètres de globalisation appropriés :  
  
    ```  
    <globalization requestEncoding="utf-8" responseEncoding="utf-8" culture="de-DE" uiCulture="en" />  
    ```  
  
3.  Enregistrez le fichier.  
  
 Lorsque vous êtes confronté à des délais d'attente pour des requêtes SQL volumineuses, il peut être nécessaire d'augmenter la valeur du délai d'expiration des services de requête.  
  
#### <a name="to-increase-the-query-service-time-out-value"></a>Pour augmenter la valeur du délai d'expiration des services de requête  
  
1.  Ouvrez le fichier web.config à l'aide du Bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, puis cliquez sur **OK**.  
  
2.  Par défaut, le délai du service de requête est de 45 secondes. Augmentez ou diminuez la valeur de l'intervalle de délai dans la ligne suivante :  
  
    ```  
    <add key="QueryServiceTimeout" value="45" />  
    ```  
  
3.  Enregistrez le fichier.  
  
 Dans un environnement multiserveur, il peut arriver qu'un serveur soit déconnecté. Lorsque cela se produit, les utilisateurs du portail peuvent être confrontés à des délais car le portail BAM ne répond plus. Pour améliorer les conditions d'utilisation du portail, vous pouvez modifier l'intervalle avant nouvelle tentative pour le serveur. Cette modification entraîne la création d'une durée minimale pendant laquelle le service Web de requête du portail BAM suppose que le serveur est déconnecté suite à un échec de connexion.  
  
 La valeur indique que si le délai défini pour une base de données locale a expiré lors d'une tentative de communication avec une base de données distante, les données sont marquées comme étant inachevées et l'ordinateur local ne tente pas de se reconnecter à la base de données distante avant que le délai indiqué ne se soit écoulé.  
  
#### <a name="to-increase-the-retry-interval-for-distributed-activities-in-a-multiserver-environment"></a>Pour augmenter l'intervalle avant nouvelle tentative dans le cas d'activités distribuées dans un environnement multiserveur  
  
1.  Ouvrez le fichier web.config à l'aide du Bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, puis cliquez sur **OK**.  
  
2.  La valeur par défaut de la propriété ServerRetryInterval est de 5 minutes. Augmentez ou diminuez la valeur de l'intervalle avant nouvelle tentative pour le serveur dans la ligne suivante :  
  
    ```  
    <add key="ServerRetryInterval" value="5"/>  
    ```  
  
3.  Enregistrez le fichier.  
  
#### <a name="to-configure-how-alert-notification-options-are-presented-in-the-bam-portal"></a>Pour configurer la présentation des options de notification d'alerte dans le portail BAM  
  
1.  Ouvrez le fichier web.config à l'aide du Bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]bamportal\web.config, puis cliquez sur **OK**.  
  
2.  Modifier le champ de valeur dans le \<ajouter la clé = « AlertNotificationOptions » value = "« /\> ligne du fichier web.config avec une liste délimitée par des virgules spécifiant les options de notification valide avec l’une des valeurs suivantes. Une valeur vide entraîne l'affichage de toutes les options de notification disponibles sur le serveur, dans l'ordre renvoyé par le serveur. Toute valeur non reconnue est équivalente à une valeur vide.  
  
    |Valeur| Description|  
    |-----------|-----------------|  
    |Fichier, Adresse de messagerie|Les options Fichier et Adresse de messagerie s'affichent. Dans la liste déroulante, l'option Fichier est affichée en premier et l'option Adresse de messagerie vient ensuite.|  
    |Adresse de messagerie, Fichier|Les options Fichier et Adresse de messagerie s'affichent. Dans la liste déroulante, l'option Adresse de messagerie est affichée en premier et l'option Fichier vient ensuite.|  
    |Fichier|Seule la notification de type Fichier est affichée dans le portail.|  
    |Email|Seule la notification de type Adresse de messagerie est affichée dans le portail.|  
  
3.  Enregistrez le fichier.  
  
## <a name="distributed-server-environments"></a>Environnements serveurs distribués  
 Si votre installation du portail BAM place les alertes et le portail BAM sur des serveurs différents, vous verrez l’erreur suivante dans le journal des événements : « System.Reflection.TargetInvocationException : Exception a été levée par la cible d’un appel de méthode. ---> Le Registre les entrées pour l’instance spécifiée de Notification Services est introuvable. »  
  
#### <a name="to-configure-the-portal-and-alerts-on-different-servers"></a>Pour configurer le portail et les alertes sur des serveurs différents  
  
1.  Ouvrez une invite de commandes.  
  
2.  Exécutez **C:\Program Files\Microsoft SQL Server\90\Notification Services\9.0.242\Bin\nscontrol register - name bamalerts-server***\<nom du serveur\>*  remplacer  *\<nom du serveur\>*  avec le nom du serveur.  
  
3.  Appuyez sur F5 pour actualiser le navigateur.  
  
## <a name="configuring-iis-to-allow-the-bam-portal-to-use-the-kerberos-network-protocol"></a>Configuration des services Internet (IIS) pour permettre au portail BAM d'utiliser le protocole réseau Kerberos  
 Si vous souhaitez utiliser le protocole réseau Kerberos avec le portail BAM, vous devez modifier la sécurité définie pour les listes de contrôle d'accès (ACL) dans le portail Web. Si les services IIS ne sont pas configurés correctement, les utilisateurs reçoivent le message d'erreur suivant :  
  
 Erreur HTTP 401.1 - non autorisé : Accès refusé en raison d’informations d’identification non valides.  
  
 Pour plus d’informations sur la modification des paramètres de sécurité IIS, consultez l’article de la Base de connaissances à [http://go.microsoft.com/fwlink/?LinkId=57922](http://go.microsoft.com/fwlink/?LinkId=57922).  
  
## <a name="viewing-aggregate-bam-data-in-the-bam-portal-in-sql-server-2008--deployments"></a>Affichage des données BAM agrégées dans le portail BAM dans les déploiements de SQL Server 2008  
 Pour afficher les données d’agrégation dans le portail BAM à partir d’un ordinateur client vers le portail BAM lors de l’environnement de déploiement utilise SQL Server 2008, vous devez installer Microsoft SQL Server 2008 Analysis Services 10.0 fournisseur OLE DB sur l’ordinateur client. Si analysis services ne sont pas installés les utilisateurs recevront un message d’erreur suivant :  
  
 Le serveur  *\<nom_serveur\>*  ne peut pas être contacté ou est trop occupé.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Planification du portail BAM](../core/planning-for-the-bam-portal.md)