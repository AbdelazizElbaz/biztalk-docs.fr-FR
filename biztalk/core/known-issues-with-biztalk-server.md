---
title: "Problèmes connus avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7998225af7ca598d4df5b4fd98f2826edce3a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-biztalk-server"></a>Problèmes connus de BizTalk Server
Cette rubrique décrit certains problèmes connus de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="dtc-firewall-rules"></a>Règles de pare-feu DTC  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts, MS DTC (Microsoft Distributed Transaction Coordinator) gère les transactions entre les ordinateurs. Vous devez donc activer les ports DTC dans vos règles de pare-feu sur les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 Lors de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les erreurs suivantes peuvent se produire lorsque les ports DTC sont désactivés dans le pare-feu :  
  
 **Erreur WMI s’est produite lors de la création de la base de données ; Essayez d’annuler et supprimer la base de données partiellement créée « SQLServerName\BizTalkMsgBoxDb »**  
  
 **Description de l’erreur WMI est générée : Exception de type « System.EnterpriseServices.TransactionProxyException » a été levée.**  
  
 Les liens suivants fournissent davantage d’informations :  
  
 [Ports pour le serveur d’Administration](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [Étapes de post-installation pour BizTalk Server 2013 et 2013 R2](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <a name="BKMK_BAM"></a>L’analyse BAM  
 Cette section énumère les problèmes connus avec le module BAM.  
  
### <a name="bam-definition-deployment-fails-due-to-a-sql-login-error"></a>Le déploiement de définition BAM échoue à cause d'une erreur de connexion SQL  
 Lors du déploiement de la définition BAM, l'opération peut échouer à cause d'une erreur de connexion (code d'erreur 42000).  
  
```  
...  
Deploying Activity... Done.   
Deploying View... ERROR: The BAM deployment failed.   
Server: The current operation was cancelled because another operation in the transaction failed.   
OLE DB error: OLE DB or ODBC error: Login failed for user <username>.; 42000.   
…  
```  
  
 Pour corriger ce problème, vérifiez que le compte de connexion SQL Analysis Services possède toutes les autorisations sur les bases de données liées à BAM.  
  
### <a name="bam-configuration-might-result-in-warnings-related-to-the-bam-analysis-logon-account"></a>La configuration BAM peut générer des avertissements liés au compte d'Analyse BAM  
 Configuration d’analyse BAM ajoute les autorisations pour le compte d’ouverture de session de l’analyse BAM dans toutes les bases de données liées à l’analyse BAM pour pouvoir y accéder. Cependant, la configuration peut ne pas réussir à réaliser cette opération et générer un avertissement si l'une des conditions préalables suivantes n'est pas remplie :  
  
-   L'utilisateur dont le compte est utilisé pour l'exécution de la configuration BAM doit être un administrateur sur l'ordinateur sur lequel Analysis Service est installé.  
  
-   L'administration à distance via le pare-feu doit être autorisée sur cet ordinateur.  
  
-   Vous pouvez également obtenir un avertissement si le compte de connexion à l'Analyse BAM est celui d'un administrateur d'un serveur SQL Server où les bases de données BAM sont installées. Vous pouvez ignorer l'avertissement et poursuivre.  
  
 **Solution de contournement** – vous devez ajouter manuellement l’autorisation pour le compte d’ouverture de session de l’analyse BAM sur toutes les bases de données liées à l’analyse BAM.  
  
### <a name="bam-portal-compatibility-with-internet-explorer-10"></a>Compatibilité du portail BAM avec Internet Explorer 10  
 Pour utiliser le portail BAM avec Internet Explorer 10, vous devez toujours utiliser le navigateur en mode Compatibilité.  
  
### <a name="receiving-notification-e-mails-even-after-the-alert-host-service-is-stopped"></a>Réception de messages électroniques de notification même après l’arrêt du service d’hôte d’alerte  
 Si vous utilisez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], vous devez configurer la fonctionnalité de messagerie de base de données dans SQL Server si vous souhaitez utiliser les alertes BAM. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise un service hôte d’alerte conjointement avec la fonctionnalité de messagerie de base de données pour envoyer des alertes de notification. Après avoir traité les notifications, le service d’hôte d’alerte transmet la charge de travail de notification au composant de messagerie de base de données dans SQL Server. Ainsi, même si vous arrêtez le service d’hôte d’alerte, il est possible que vous receviez des notifications pour des événements qui ont été traités par ce service mais pas par le composant de messagerie de base de données.  
  
### <a name="configuring-tracing-for-bam-alerts"></a>Configuration du suivi pour les alertes BAM  
 Si vous utilisez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], et que vous souhaitez activer le suivi de diagnostic pour les alertes BAM, vous devez le faire en créant un fichier de configuration pour l’hôte des alertes BAM. Vous devez nommer le fichier **BAMAlerts.exe.config** et copiez-le vers le même emplacement que le fichier EXE (**BAMAlerts.exe**), qui est à \Program Files\Microsoft BizTalk Server\Tracking\\.  
  
 Un exemple de fichier de configuration se présente de la manière suivante. Ce fichier enregistre les **informations** détails de l’Observateur d’événements de niveau.  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <a name="BKMK_Upgrade"></a>Problèmes rencontrés lors de l’utilisation de BizTalk Server avec SQL Server 2012  
 Lors de l’utilisation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] que vous pouvez définir le **Remote Login Timeout** valeur dans SQL Server à 20 secondes. Si vous ne le faites pas, vous risquez de rencontrer des erreurs dans des situations de stress. Pour obtenir des instructions sur la façon de définir la valeur de délai d’attente de connexion à distance dans [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], consultez [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)  
  
##  <a name="BKMK_Adapters"></a>Problèmes avec les cartes  
 Cette section énumère les problèmes connus rencontrés avec les adaptateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="dynamic-port-may-fail-while-using-the-windows-sharepoint-services-wss-adapter"></a>Le port dynamique peut échouer au cours de l’utilisation de l’adaptateur WSS (Windows SharePoint Services)  
 Un port dynamique utilisant l’adaptateur WSS peut échouer avec l’erreur suivante :  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 **Solutions de contournement**:  
  
-   Dans la configuration du port, pour l’URL de site, indiquez également le numéro de port, Par exemple, `http://server:80/site`.  
  
-   Activer la **Windows Identity Foundation 3.5** fonctionnalité.  
  
-   Confirmer le compte de l’hôte BizTalk en cours d’exécution a accès à SharePoint.  
  
### <a name="adapters-available-with-biztalk-adapter-pack-cannot-be-administered-on-a-computer-that-only-has-biztalk-server-administration-component-installed"></a>Les adaptateurs disponibles avec le Pack d’adaptateurs BizTalk ne peuvent pas être administrés sur un ordinateur sur lequel seul le composant Administration de BizTalk Server est installé.  
 Si le Pack d’adaptateurs BizTalk est installé sur un ordinateur sur lequel seule la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installée, les adaptateurs installés dans le cadre du Pack d’adaptateurs BizTalk ne sont pas disponibles lorsque vous créez un port d’envoi ou un emplacement de réception. En effet, les adaptateurs dépendent du composant d’exécution BizTalk pour être installés sur le même ordinateur.  
  
 Contournement du problème : installez le composant d’exécution BizTalk Server sur l’ordinateur où sont installés le Pack d’adaptateurs et le composant Administration de BizTalk Server. Il n’est pas nécessaire de configurer BizTalk Server sur cet ordinateur.  
  
## <a name="other-issues"></a>Autres problèmes  
  
### <a name="setupbat-for-biztalk-server-samples-runs-with-a-32-bit-command-prompt"></a>Setup.bat pour les exemples BizTalk Server s’exécute avec une invite de commande 32 bits.  
 Pour les exemples [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclus dans cette version, vous devez exécuter les fichiers setup.bat associés à partir d’une invite de commande 32 bits uniquement. L’exécution des fichiers de lot à partir d’une invite de commande 64 bits peut entraîner un échec.  
  
### <a name="run-setup-as-administrator"></a>Exécuter l'installation en tant qu'administrateur  
 Lors de l’installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], utilisez le **exécuter en tant qu’administrateur** option. Sinon, les erreurs suivantes peuvent se produire :  
  
 Erreur interne 2761. Code de retour : 1  
  
 Installation MSI retournée 1603 - Erreur irrécupérable pendant l’installation.  
  
### <a name="using-certificates-with-1024-key-for-encoding-and-signing-results-in-failure-of-mime-smime-decoding"></a>L’utilisation de certificats avec une clé 1024 pour le codage et la signature entraîne l’échec du décodage MIME-SMIME.  
 Sur Windows 8, lorsqu’un message est chiffré et signé à l’aide de certificats avec une clé 1024, le décodage MIME-SMIME ne parvient pas à authentifier le message. Pour éviter ce problème, vous pouvez utiliser des certificats avec une clé 2048.  
  
### <a name="uddi-resolver-with-esb-toolkit-gives-a-serialization-error"></a>L’outil de résolution UDDI avec ESB Toolkit génère une erreur de sérialisation  
 Lors de l’utilisation des services UDDI avec [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)], vous risquez de rencontrer une erreur de sérialisation XML lors de la recherche des détails de la liaison. Cette erreur se produit si la clé de liaison n’est pas spécifiée.  
  
### <a name="the-itinerary-designer-for-esb-toolkit"></a>Concepteur d’itinéraire pour ESB Toolkit  
 Le concepteur d’itinéraire pour [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] fait désormais partie du support d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez trouver le concepteur d’itinéraire dans le dossier racine du support, nommé `Microsoft.Practices.Services.Itinerary.DslPackage.vsix`. Auparavant, ce fichier était disponible à l’emplacement où vous avez installé [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)], qui est généralement \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
### <a name="edi"></a>Routage  
 Le traitement par lot EDI est utilisé. Lors de l’utilisation d’un calendrier arabe ou de paramètres locaux arabes, l’orchestration s’interrompt en générant l’erreur suivante :  
  
 **Code d’erreur : 0xC0C01B52 (erreur du moteur d’Orchestration) Description de l’erreur : interruption due à un échec de persistance au cours de la mise en attente.** Calendrier grégorien arabe prend en charge les dates à partir de *30/04/1900 00.00.00* à *13/05/2029 23:59:59*.  
  
 Pour résoudre ce comportement, entrez une date de fin arabe valide.  
  
### <a name="enterprise-single-sign-on"></a>Enterprise Single Sign-On  
 Lorsque vous installez l'authentification unique de l'entreprise ou lorsque vous redémarrez le service d'authentification unique de l'entreprise, il est possible que l'erreur suivante soit consignée dans l'Observateur d'événements.  
  
 **Impossible de charger \Program code d’erreur Sign-on\ssopsserver.dll Files\Enterprise : 0x8007007E, le module spécifié est introuvable.** Vous pouvez ignorer cette erreur sans problème.