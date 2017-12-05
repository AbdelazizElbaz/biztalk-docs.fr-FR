---
title: "L’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf420061-41d1-4d97-9be1-403cd101e41c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e403121b02ecbfee4880328747aaba3fc175a322
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-a-custom-web-part-with-oracle-e-business-suite"></a>L’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite
Cette section fournit des informations sur l’utilisation d’un composant WebPart personnalisé avec Microsoft Office SharePoint Server. Pour utiliser un composant WebPart personnalisé, vous devez procédez comme suit :  
  
1.  Créer un composant WebPart personnalisé  
  
2.  Déployer le composant WebPart personnalisé à un portail SharePoint  
  
3.  Configurer le portail SharePoint pour utiliser le composant WebPart personnalisé  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Avant de créer un composant WebPart personnalisé :  
  
-   Publier les artefacts d’Oracle E-Business Suite comme un service WCF. Pour plus d’informations, consultez [étape 1 : utiliser l’adaptateur Oracle E-Business pour créer et publier un service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md) dans [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
-   Créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite à l’aide du catalogue de données métiers dans Microsoft Office SharePoint Server. Pour plus d’informations, consultez [étape 2 : créer un fichier de définition d’application pour les artefacts d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) dans [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).  
  
##  <a name="Create_a_Custom_Web_Part"></a>Étape 1 : Créer un composant WebPart personnalisé  
  
1.  Démarrez Visual Studio et puis créer un projet.  
  
2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** volet, sélectionnez **Visual C#**. À partir de la **modèles** volet, sélectionnez **bibliothèque de classes**.  
  
3.  Spécifiez un nom et l’emplacement de la solution. Pour cette rubrique, vous devez spécifier `CustomWebPart` dans les **nom** et **nom de la Solution** cases. Spécifiez un emplacement, puis cliquez sur **OK**.  
  
4.  Ajoutez une référence au composant System.Web dans le projet. Cliquez sur le nom du projet dans **l’Explorateur de solutions**, puis cliquez sur **ajouter une référence**. Dans le **ajouter une référence** boîte de dialogue, sélectionnez **System.Web** dans les **.NET** onglet, puis cliquez sur **OK**. Le composant de System.Web contient l’espace de noms requis de System.Web.UI.WebControls.WebParts.  
  
5.  Ajoutez le code requis en fonction de votre problème dans le projet. Pour l’exemple de code qui s’applique à un problème de certain, consultez « Problèmes qui impliquent des composants WebPart personnalisés » dans [considérations relatives à l’utilisation de l’adaptateur Oracle-Business Suite avec SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/considerations-using-the-oracle-business-suite-adapter-with-sharepoint.md).  
  
6.  créer le projet ; Build réussie du projet, un fichier .dll, CustomWebPart.dll, est généré dans le \<dossier du projet \> /bin/Debug dossier.  
  
7.  **Uniquement pour un ordinateur 64 bits**: signer le fichier CustomWebPart.dll avec un nom fort avant d’effectuer les étapes suivantes. Dans le cas contraire, vous ne serez pas en mesure d’importer et utilisent donc le CustomWebPart.dll dans le portail SharePoint dans « étape 3 : configurer le portail SharePoint pour utiliser le composant WebPart personnalisé. » Pour plus d’informations sur la façon de signer un assembly avec un nom fort, consultez [Comment : signer un Assembly avec un nom fort](https://msdn.microsoft.com/library/xc31ft41.aspx).
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a>Étape 2 : Déployer le composant WebPart personnalisé à un portail SharePoint  
 Vous devez effectuer les opérations suivantes pour rendre le fichier CustomWebPart.dll (composant WebPart personnalisé) qui est créé dans « étape 1 : créer un composant WebPart personnalisée » de cette rubrique utilisable sur le portail SharePoint :  
  
-   **Copiez le fichier CustomWebPart.dll dans le dossier bin du portail SharePoint**: Microsoft Office SharePoint Server crée des portails sous la \<racine du lecteur\>: \Inetpub\wwwroot\wss\VirtualDirectories dossier. Un dossier est créé pour chaque portail et peut être identifié avec le numéro de port. Vous devez copier le fichier CustomWebPart.dll créé dans « étape 1 : créer un composant WebPart personnalisée » de cette rubrique pour le \<racine du lecteur\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< numéro_port\>dossier \bin. Par exemple, si le numéro de port de votre portail SharePoint est 13614, vous devez copier le fichier CustomWebPart.dll à la \<racine du lecteur\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin dossier.  
  
    > [!TIP]
    >  Une autre consiste à trouver l’emplacement du dossier de votre portail SharePoint à l’aide de la **Gestionnaire des Services Internet (IIS)** fenêtre (**Démarrer** > **exécuter**  >  **inetmgr**). Recherchez votre portail SharePoint dans le **Gestionnaire des Services Internet (IIS)** fenêtre ([nom_ordinateur] > Sites Web > [nom-portail]), avec le bouton droit, puis cliquez sur **propriétés** dans le menu contextuel. Dans la boîte de dialogue Propriétés du portail SharePoint, cliquez sur le **répertoire de base** onglet, puis sélectionnez le **chemin d’accès Local** boîte.  
  
-   **Ajoutez l’entrée de contrôle sécurisé dans le fichier web.config**: étant donné que le fichier CustomWebPart.dll sera utilisé sur des ordinateurs différents et par plusieurs utilisateurs, vous devez déclarer le fichier en tant que « safe ». Pour ce faire, ouvrez le fichier web.config situé dans le dossier portail SharePoint à \<racine du lecteur\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< numéro_port\>. Sous le `<SafeControls>` section du fichier web.config, ajoutez l’entrée de contrôle sécurisé suivante :  
  
    -   **Sur un ordinateur 32 bits :**  
  
        ```  
        <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
    -   **Sur un ordinateur 64 bits :**  
  
        ```  
        <SafeControl Assembly="CustomWebPart, Version=1.0.0.0, Culture=neutral, PublicKeyToken=<PUBLICKKEYTOKEN_OF_CustomWebPart.dll>" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
     Enregistrez le fichier web.config et fermez-le.  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a>Étape 3 : Configurer le portail SharePoint pour utiliser le composant WebPart personnalisé  
 Vous devez ajouter le composant WebPart personnalisé pour Microsoft Office SharePoint Server Web Part Gallery, afin que vous puissiez l’utiliser sur votre portail SharePoint. Pour cela :  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom de la Service fournisseur partagés (SSP) à laquelle vous souhaitez ajouter le composant WebPart personnalisé.  
  
3.  Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
4.  Dans la page Paramètres du Site, cliquez sur **WebPart** sous le **galeries** colonne.  
  
5.  Dans la page Galerie de composants WebPart, pour ajouter le composant WebPart personnalisé à la galerie, cliquez sur **nouveau**. À ce stade, le composant WebPart personnalisé n’est pas disponible dans la page Galerie de composants WebPart.  
  
6.  Sur la page de nouveaux composants WebPart, localisez **CustomWebPart** (nom du composant WebPart personnalisé) dans la liste, sélectionnez la case à cocher sur la gauche, puis cliquez sur **compléter la galerie** en haut de la page. Cette opération ajoute le **CustomWebPart** entrée dans la page Galerie de composants WebPart.  
  
 Vous pouvez maintenant utiliser le composant WebPart personnalisé (**CustomWebPart**) pour créer des composants WebPart dans votre portail SharePoint. Le composant WebPart personnalisé (**CustomWebPart**) s’affiche sous le **divers** section dans la page Ajouter des composants WebPart.  
  
## <a name="see-also"></a>Voir aussi  
[Utilisez l’adaptateur Oracle E-Business Suite avec SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)