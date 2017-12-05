---
title: "Procédure pas à pas : Personnalisé traitement du Message avec l’adaptateur WCF-NetTcp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b56b7492-2ea0-4c63-8f1b-430eb277517d
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a7123d908f25e6575eaaba4f9a92608f17c88be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-custom-message-processing-with-the-wcf-nettcp-adapter"></a>Procédure pas à pas : Personnalisé traitement du Message avec l’adaptateur WCF-NetTcp
Dans cette procédure pas à pas, un client [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] soumet un message [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] contenant des données d'image JPEG binaires imbriquées à un emplacement de réception BizTalk à l'aide de l'adaptateur WCF-NetTcp. L’image JPEG codée en binaire est extraite à l’aide d’une instruction XPath (avec codage de nœud Base64) via le **corps du Message entrant** paramètres de configuration de l’adaptateur. Un traitement XPath diffère de la méthode par défaut que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour gérer les messages entrants. Dans la méthode par défaut, l’adaptateur obtient le contenu entier de la **corps** élément de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de message, puis l’envoie à la base de données MessageBox de BizTalk. Le traitement de message XPath extrait des éléments spécifiques d'un message [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] entrant pour créer un message BizTalk personnalisé. Dans cet exemple, le traitement XPath localise un élément XML nommé **SendPicture** en entrant [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message (qui est au format XML). Après avoir trouvé cet élément, XPath en extrait la valeur sous forme d'objet Base64 codé en binaire, puis place cette valeur binaire dans un message BizTalk. Le message est publié dans la base de données MessageBox, puis transféré vers un port d'envoi FILE à l'aide d'un abonnement de filtre de port d'envoi. Cet exemple n'utilise aucune orchestration. Tout le traitement est effectué via la messagerie BizTalk à l'aide de XPath.  
  
 Un adaptateur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] est utilisé pour communiquer avec les clients [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] et les services à distance [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  Il permet la publication d'orchestrations et de schémas en tant que services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], et offre à une orchestration la possibilité d'utiliser des services WCF externes. L’adaptateur WCF-NetTcp utilise la **NetTcpBinding** liaison, ce qui signifie que le transport TCP à l’aide d’un encodage de message binaire optimisé. L'adaptateur WCF-NetTcp consiste en un adaptateur d'envoi et un adaptateur de réception. Il fournit un accès total aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP.  
  
 Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   À l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], importer un fichier MSI pour créer un port d'envoi, un port de réception et un emplacement de réception.  
  
-   À l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, configurez un [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] emplacement de réception pour exécuter une instruction XPath pour extraire les données à partir de la **SendPicture** élément de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message.  
  
> [!NOTE]
>  Le **hosttrusted** élément spécifie si l’hôte associé au Gestionnaire de réception est approuvé. Dans le fichier bindings.xml, il est défini sur son paramètre par défaut, `false`, parce que, dans cet exemple, nous ne nous préoccupons pas du service d''authentification unique de l'entreprise (SSO) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce dernier permet la transmission d'informations d'identification utilisateur par le biais de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'intégration d'applications de tierce partie avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Un paramètre `false` empêche le transit d'un message BizTalk via le service BizTalk dans le cadre du traitement d'authentification unique.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cet exemple, assurez-vous que votre environnement installe les composants requis suivants :  
  
-   L’ordinateur qui génère les assemblys et exécute le processus de déploiement et l’ordinateur qui exécute l’exemple, requièrent Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]et Microsoft BizTalk Server.  
  
-   L’ordinateur utilisé pour générer les assemblys et exécuter le processus de déploiement requiert Microsoft Visual Studio.  
  
-   L'ordinateur qui exécute l'exemple requiert les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les outils d'administration de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il s’agit des options d’installation lors de l’installation de Microsoft BizTalk Server.  
  
-   Sur les ordinateurs utilisés pour effectuer des tâches d'administration, vous devez exécuter un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer les paramètres d'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'intérieur de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce compte d'utilisateur doit également être membre du groupe Administrateurs local pour le déploiement d'application, la gestion d'instances de l'hôte et d'autres tâches éventuellement requises.  
  
-   Sur n’importe quel ordinateur qui nécessite [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité, effectuez la procédure d’installation unique pour le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exemples [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
-   Sur l'ordinateur qui exécute l'exemple et importe un fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous que l'hôte n'est pas approuvé, sans quoi l'importation échoue.  
  
-   Vous devez télécharger le code de procédure pas à pas et l’extraire sur votre ordinateur.  Cette procédure pas à pas est une partie de l’ensemble du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] package de la procédure pas à pas de carte. Vous pouvez télécharger le fichier **WCFAdapterWalkthroughs.exe** à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] centre de développement sur [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
### <a name="configure-the-wcfcustommessageprocessing-application-and-artifacts"></a>Configuration de l'application WCFCustomMessageProcessing et d'artefacts  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **Applications**, sélectionnez **importation**, puis sélectionnez **fichier MSI**. Accédez à la **C:\WCFCustomMessageProcessing\WCFCustomMessageProcessing.msi** de fichiers, puis cliquez sur **ouvrir**. Cela crée les artefacts suivants pour cette application :  
  
    -   **FileSP** port d’envoi : l’emplacement sur le système de fichiers local **C:\WCFCustomMessageProcessing\Out** où les données d’image JPEG sont envoyées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en tant que la sortie finale de l’exemple de traitement. Vous pouvez afficher le filtre de port d’envoi **BTS. RecievePortName = NetTcpRP** configuré dans le **FileSP Properties** boîte de dialogue sous **filtres**. Le filtre est associé au port de réception NetTcp. Emplacement de sortie du port d’envoi tout message accepté sur NetTcpRP port de réception est envoyé à la FileSP **C:\WCFCustomMessageProcessing\Out** après le traitement XPath sur le message de l’exécution de l’emplacement de réception.  
  
    -   **NetTcpRP** port de réception : le port qui contient logiquement le **NetTcpRL** emplacement de réception.  
  
    -   **NetTcpRL** emplacement de réception : il utilise la valeur par défaut **PassThroughTransmit** données entrant d’image de pipeline et l’adaptateur WCF-NetTcp pour exécuter une instruction XPath pour extraire l’image JPEG [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message.  
  
### <a name="alternative-steps-to-configure-the-wcfcustommessageprocessing-application"></a>Autres étapes pour configurer l'application WCFCustomMessageProcessing  
  
-   Ou bien, voici la procédure manuelle pour configurer l’application sans utiliser le **C:\WCFCustomMessageProcessing\bindings.xml** fichier. Il est inutile de les exécuter si le processus d'importation de fichier de liaison précédent fonctionne correctement.  En revanche, la lecture de ces étapes enrichira probablement votre connaissance de l'utilité du fichier MSI.  
  
-   Créer un port de réception unidirectionnel (**NetTcpRP**) et un emplacement de réception (**NetTcpRL**).  
  
    1.  Développez le **WCFCustomMessageProcessing** application, avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **Port de réception unidirectionnel**. Dans le **propriétés du Port de réception** boîte de dialogue, entrez `NetTcpRP` pour **nom**, puis cliquez sur **OK**.  
  
    2.  Avec le bouton droit le **NetTcpRP** port de réception, sélectionnez **nouveau**, puis sélectionnez **un emplacement de réception**. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez `NetTcRL` pour **nom**. Dans le **Transport** , cliquez sur le **Type** zone de liste déroulante, sélectionnez **WCF-NetTcp** dans la liste déroulante, puis cliquez sur **configurer**.  
  
    3.  Sur le **général** , entrez **NET.TCP://localhost/nettcprl/image** dans les **adresse (URI)** champ.  
  
    4.  Sur le **sécurité** onglet, définissez la **mode de sécurité** à **None.**  
  
    5.  Sur le **Message** onglet, sélectionnez le **chemin d’accès** est définie sur le **le corps du message BizTalk entrant**et entrez `/*[local-name()="SendPicture" and namespace-uri()='http://tempuri.org/']/*[local-name()="stream"]` pour l’expression de chemin de corps. Sélectionnez **Base64** comme le **codage de nœud**. Le **chemin d’accès** option est définie sur la valeur, car le corps de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit est au format suivant :   **\<SendPicture xmlns = « http:// tempuri.org/ «\>\<flux\>*réel base 64 encodé des données image binaires*\</stream\>\</SendPicture\>**  
  
    6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
-   Créez un port d'envoi de fichier unidirectionnel (FileSP) abonné au port de réception NetTcpRP.  
  
    1.  Avec le bouton droit **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port de réception unidirectionnel**. Sélectionnez **Port statique unidirectionnel**. Entrez `FileSP` pour **nom**.  
  
    2.  Dans le **Transport** , cliquez sur le **Type** zone de liste déroulante, sélectionnez **fichier** dans la liste déroulante, puis cliquez sur **configurer**.  
  
    3.  Sous **dossier de Destination** entrez `C:\WCFCustomMessageProcessing\Out`, puis cliquez sur **OK**.  
  
    4.  Cliquez sur **filtres**, sélectionnez `BTS.ReceivePortName == NetTcpRP`, puis cliquez sur **OK.**  
  
### <a name="configure-the-send-port-and-run-the-application"></a>Configuration du port d'envoi et exécution de l'application  
  
1.  Cliquez sur le **WCFCustomMessageProcessing** application et sélectionnez **Démarrer**. Cela a pour effet d'inscrire l'emplacement de réception NetTcpRL et de démarrer le port d'envoi FileSP.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le `Client.sln` de fichiers à partir de la **c : wcfcustommessageprocessing\client** dossier. Dans l’Explorateur de solutions, cliquez sur le **Client** de projet et sélectionnez **Build**.  
  
3.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], sélectionnez **déboguer**, puis sélectionnez **démarrer sans débogage** pour exécuter l’application Client.exe. Une invite de commandes s'affiche, indiquant que l'image a été soumise à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
4.  Observez la sortie du fichier {GUID} .jpg réussie dans le dossier de fichiers de port envoi de **C:\WCFCustomMessageProcessing\Out**. Celle-ci indique que le traitement d'application pour extraire le fichier JPEG et l'écrire dans un port d'envoi FILE a réussi.