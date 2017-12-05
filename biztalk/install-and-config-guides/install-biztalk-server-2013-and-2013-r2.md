---
title: Installer BizTalk Server 2013 et 2013 R2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4665ea-6f2c-477f-98ec-1cebef05ad4a
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e04bbce8870e4f0e8c0edb278511f2a6791d62d8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-biztalk-server-2013-and-2013-r2"></a>Installation de BizTalk Server 2013 et 2013 R2
Énumère les étapes pour installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="before-you-get-started"></a>Avant de commencer

-   **Noms de comptes** – Dans la mesure du possible, utilisez les noms de comptes par défaut. Le programme d'installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] entre automatiquement les comptes par défaut. Si le domaine contient plusieurs groupes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], changez les noms des comptes afin d'éviter les conflits. Si vous modifiez les noms, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend uniquement en charge \< *nom de domaine NetBIOS*\>\\<*utilisateur* \> pour le service les comptes et groupes Windows.  
  
-   **Noms de comptes avec le service Web de gestion BAM** – [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge les comptes intégrés ni les comptes sans mot de passe pour l’utilisateur de service Web de gestion BAM. Le service Web accède à la base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ces comptes peuvent suggérer une menace sur la sécurité.  
  
    > [!NOTE]
    >  Même si la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec ces types de comptes réussit, le service Web de gestion BAM échoue. Des comptes intégrés ou des comptes sans mot de passe peuvent être utilisés pour le pool d'applications BAM.  
  
-   **BizTalk Assembly Viewer** – Non pris en charge sur une plateforme 64 bits.  
  
-   **Installation et désinstallation** – La désinstallation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] demande la suppression manuelle des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en tant que développeur ou évaluateur, utilisez une machine virtuelle. Si vous avez besoin de réinstaller, vous pouvez facilement restaurer la machine virtuelle sans avoir à désinstaller et à supprimer les bases de données.  
  
-   **Ordinateurs 32 bits et 64 bits** – L’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur des ordinateurs 32 bits et 64 bits présente quelques différences. La procédure d'installation et de configuration couvre les ordinateurs 32 bits et 64 bits. Les différences éventuelles sont signalées.  
  
-   **Groupes de travail** – L’installation et la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l’environnement de groupe de travail sur un seul ordinateur sont prises en charge. Les fonctionnalités et composants de SQL Server et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont installés et configurés sur le même ordinateur.  
  
-   **Terminal Server** – L’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide de Terminal Server en mode application n’est pas prise en charge. Consultez [KB 832027](http://support.microsoft.com/kb/832027).  
  
-   **Portail BAM** – Si le portail BAM est configuré sur un site web utilisé par des applications qui exécutent .NET Framework 2.0, créez un nouveau site web pour le portail BAM :  
  
     [Création d’un site web IIS 7](http://technet.microsoft.com/library/cc772350\(WS.10\).aspx)  
  
     [Création d’un site web IIS 8](http://technet.microsoft.com/library/hh831515.aspx)  
  
     Après la création du nouveau site Web :  
  
    1.  Ouvrez **Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**.  
  
    2.  Reconfigurez le portail BAM et sélectionnez le nouveau site web dans la liste **Site Web du portail BAM**.  
  
-   **Ajouts de la communauté** : Lisez :  
  
     [Proactivité dans BizTalk Server](http://msdn.microsoft.com/library/dn393929\(v=bts.10\).aspx)  
  
     [BizTalk Server 2013 R2 : Installation et configuration – Considérations importantes avant de configurer le serveur (partie 1)](http://sandroaspbiztalkblog.wordpress.com/2015/01/04/biztalk-server-2013-r2-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)  
  
##  <a name="BKMK_Install"></a> Installation de BizTalk Server  
  
1.  Fermez tous les programmes ouverts. Exécutez le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en tant qu'administrateur.  
  
2.  Dans **Démarrer**, sélectionnez **Installer Microsoft BizTalk Server**.  
  
3.  Dans **Informations sur le client**, entrez votre nom d’utilisateur, votre organisation, votre clé de produit, puis sélectionnez **Suivant**.  
  
4.  Dans **Contrat de Licence**, acceptez le contrat de licence, puis sélectionnez **Suivant**.  
  
5.  Dans **Programme d’amélioration du produit**, choisissez votre préférence de participation, puis sélectionnez **Suivant**.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] participe au Programme d'amélioration du produit. Vous pouvez choisir d'envoyer des commentaires utiles à Microsoft en ce qui concerne la fonctionnalité de création de rapports d'utilisation des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les données ainsi collectées sont anonymes et ne peuvent pas être utilisées pour vous identifier. Dans le cadre de ce programme, Microsoft collecte des statistiques d'utilisation des fonctions. En participant à ce programme, vous pouvez contribuer à améliorer la fiabilité et les performances de diverses fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur ce programme et sa politique de confidentialité, consultez la rubrique [Politique de confidentialité de Microsoft BizTalk Server CEIP](http://go.microsoft.com/fwlink/p/?LinkId=188553).  
  
6.  Dans **Installation des composants**, passez en revue les composants disponibles et sélectionnez ceux que vous souhaitez installer :  

    |Fonctionnalité|Description|  
    |-------------|-----------------|  
    |**Documentation**|Documentation principale, didacticiels, référence de l’interface utilisateur (Aide F1), référence du programmeur ainsi que les instructions d’utilisation pour les utilitaires et les exemples SDK.|  
    |**Moteur d’exécution BizTalk Server**|Services d’exécution essentiels pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**Composant d’exécution BizTalk EDI/AS2**|Services d’exécution offrant une prise en charge native des échanges de données informatisés (EDI, Electronic Data Interchange) et de la fonctionnalité d’envoi de messages par protocole AS2 (Applicability Statement 2). **Remarque :** Vous ne pouvez sélectionner cette option que si vous avez sélectionné la fonctionnalité **Moteur d’exécution BizTalk Server**.|  
    |**Composant d’exécution de l’adaptateur Windows Communication Foundation (WCF)**|Adaptateurs permettant à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de communiquer avec des applications WCF. **Remarque :** Vous ne pouvez sélectionner cette option que si vous avez sélectionné la fonctionnalité **Moteur d’exécution BizTalk Server**.|  
    |**Composants du portail**|Les composants du portail constituent un ensemble de fonctionnalités utilisées par les analystes d’entreprise pour communiquer, collaborer et prendre des décisions à l’aide de données d’entreprise.|  
    |**Analyse BAM**|Cet ensemble de fonctionnalités offre aux utilisateurs d’entreprise une vue en temps réel de leurs différents processus d’entreprise hétérogènes, leur permettant ainsi de prendre d’importantes décisions commerciales. **Remarque :** Vous ne pouvez sélectionner cette option que si vous avez sélectionné la fonctionnalité **Composants du portail**.|  
    |**Outils d’administration et surveillance**|Composants nécessaires à l’administration et la surveillance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l’ordinateur local et sur le serveur distant.|  
    |**Outils d’administration WCF (Windows Communication Foundation)**|La sélection de cette fonctionnalité installe les services administratifs des composants WCF. **Remarque :** Vous ne pouvez sélectionner cette option que si vous avez sélectionné la fonctionnalité **Outils d’administration et surveillance**.|  
    |**Outils et kit de développement**|Exemples et utilitaires permettant de créer rapidement des solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], comprenant la documentation et les exemples SDK, les concepteurs de schémas et de mappages, ainsi que les modèles de projet Visual Studio. **Important :** Vous devez installer ce composant si vous envisagez d’effectuer un travail de développement. Les extensions Visual Studio utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne fonctionnent pas si le composant **Outils et kit de développement** n’est pas installé.|  
    |***Logiciels complémentaires***||  
    |**Administration de l’authentification unique de l’entreprise**|Interface de gestion des applications associées SSO et de leurs mappages.|  
    |**Serveur de secret principal du système d’authentification unique de l’entreprise**|Serveur SSO qui stocke le secret principal. Tous les autres serveurs SSO du système obtiennent le secret principal à partir de ce serveur. Le serveur de secret principal est requis dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**Composants des règles d’entreprise**|permettent de composer les stratégies utilisées par le moteur des règles d'entreprise.|  
    |**MQSeries Agent**|permet la communication entre l'adaptateur BizTalk pour MQSeries et MQSeries Server pour Windows.|  
    |**Service Web Adaptateur Windows SharePoint Services**|**Déconseillé**. À l’aide d'un service Web IIS installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] traite les documents entrants et sortants via Microsoft SharePoint.<br /><br /> **Recommandation** : Ne les installez **pas**. Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le composant redistribuable du modèle CSOM SharePoint installé automatiquement sur le serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], comme décrit dans l’[Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).|  
    |**Fournisseur d’alertes BAM**|Configure les Alertes BAM<br /><br /> Lorsque vous utilisez les alertes BAM avec [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] ou [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] SP1, vous devez configurer la fonctionnalité de messagerie de base de données. La fonctionnalité SQL Server Notification Services ne peut pas être utilisée.|  
    |**Client BAM**|logiciel côté client qui permet aux utilisateurs d'entreprise d'utiliser l'analyse BAM.|  
    |**BAM-Événements**|Intercepteurs pour Windows Workflow Foundation et Windows Communication Foundation. Inclut également l'API d'événements BAM, qui envoie les événements vers la base de données BAM à partir d'applications personnalisées.|  
    |**Composant de création de projet**|Outil qui vous permet de créer des solutions [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sans utiliser Visual Studio.|  

7. Acceptez l’emplacement d’installation par défaut ou sélectionnez **Parcourir** pour indiquer un autre emplacement où installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Sélectionnez **Suivant**.  
  
8.  S’il manque un composant requis sur votre ordinateur (par exemple, ADOMD.NET), le programme d’installation peut installer les composants redistribuables requis. Vous pouvez effectuer l'une des opérations suivantes :  
  
    -   Sélectionnez **Installer automatiquement la configuration requise redistribuable à partir du Web**  
    
         - ou -  
  
    -   Sélectionnez **Installer automatiquement la configuration requise redistribuable à partir d’un fichier CAB**, si vous avez téléchargé le fichier CAB. En sélectionnant la seconde option, vous pouvez accéder à l'emplacement du fichier CAB.  
  
9.  Dans la page **Résumé**, vérifiez que les composants sont corrects. Pour activer la connexion automatique après un redémarrage système, sélectionnez **Définir** et entrez le compte de connexion. L'ouverture de session automatique est uniquement activée pour les redémarrages durant l'installation ; elle est désactivée lorsque l'installation prend fin.  
  
10. Sélectionnez **Installer** pour démarrer le processus d’installation.  
  
11. Dans **Configuration de Microsoft Update**, indiquez votre préférence, puis sélectionnez **Suivant**.  
  
12. Dans **Installation terminée**, décochez la case **Lancer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, puis sélectionnez **Terminer**.  
  
## <a name="additional"></a>Supplément  
  
-   Lorsque vous avez installé SQL Server, le programme d’installation de SQL Server a accordé à votre compte de connexion des droits d’administrateur système. Comme ces droits sont également requis pour l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez effectuer l'une des actions suivantes :  
  
    -   Utilisez le compte utilisé lors de l'installation de SQL Server.  
  
    -   Accordez des droits d’administrateur système au compte de connexion.  
  
-   Après avoir téléchargé le fichier EXE auto-extractible pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le guide d'installation s'ouvre. Le fichier Setup.exe pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se trouve dans le même emplacement que celui du guide d'installation.  
  
-   Au lieu d'installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur physique, vous pouvez choisir de configurer une machine virtuelle [!INCLUDE[winazure](../includes/winazure-md.md)] avec une image [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez [Configuration de BizTalk Server sur une machine virtuelle Azure](http://msdn.microsoft.com/library/azure/jj248689.aspx).  
  
-   Pour connaître les étapes d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide d’une invite de commandes, consultez l’[Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md).  
  
 
## <a name="see-also"></a>Voir aussi  
   
 [Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md)   
 [Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [Annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md)