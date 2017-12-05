---
title: "Utiliser un composant WebPart personnalisé avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3a6c04-6523-483c-bdf4-ce0ac47cda87
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ad29a3ad28fcea81b00b6b2e2dabf51f0962e79
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-a-custom-web-part-with-the-siebel-adapter"></a>Utiliser un composant WebPart personnalisé avec l’adaptateur Siebel
Cette section fournit des informations sur l’utilisation d’un composant WebPart personnalisé avec Microsoft Office SharePoint Server. Pour utiliser un composant WebPart personnalisé, vous devez procédez comme suit :  
  
1.  Créer un composant WebPart personnalisé  
  
2.  Déployer le composant WebPart personnalisé à un portail SharePoint  
  
3.  Configurer le portail SharePoint pour utiliser le composant WebPart personnalisé  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Avant de créer un composant WebPart personnalisé :  
  
-   Publier les artefacts Siebel sous la forme d’un service WCF. Pour plus d’informations, consultez [étape 1 : publier les opérations de composant d’entreprise Siebel comme Service WCF](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md) dans [didacticiel 1 : présentation sur un SharePoint Site de données à partir de système Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
-   Créer un fichier de définition d’application pour les artefacts de Siebel à l’aide du catalogue de données métiers dans Microsoft Office SharePoint Server. Pour plus d’informations, consultez [étape 2 : créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md) dans [didacticiel 1 : présentation sur un SharePoint Site de données à partir de système Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
##  <a name="Create_a_Custom_Web_Part"></a>Étape 1 : Créer un composant WebPart personnalisé  
 Pour créer un composant WebPart personnalisé à l’aide de Visual Studio, procédez comme suit :  
  
1.  Démarrez Visual Studio et puis créer un projet.  
  
2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** volet, sélectionnez **Visual C#**. À partir de la **modèles** volet, sélectionnez **bibliothèque de classes**.  
  
3.  Spécifiez un nom et l’emplacement de la solution. Pour cette rubrique, vous devez spécifier `CustomWebPart` dans les **nom** et **nom de la Solution** cases. Spécifiez un emplacement, puis cliquez sur **OK**.  
  
4.  Ajoutez une référence au composant System.Web dans le projet. Cliquez sur le nom du projet dans **l’Explorateur de solutions**, puis cliquez sur **ajouter une référence**. Dans le **ajouter une référence** boîte de dialogue, sélectionnez **System.Web** dans les **.NET** onglet, puis cliquez sur **OK**. Le composant de System.Web contient l’espace de noms requis de System.Web.UI.WebControls.WebParts.  
  
5.  Ajoutez le code requis en fonction de votre problème dans le projet. Pour l’exemple de code qui s’applique à un problème de certain, consultez « Problèmes qui impliquent des composants WebPart personnalisés » dans [considérations sur l’utilisation de l’adaptateur Siebel avec SharePoint](../../adapters-and-accelerators/adapter-siebel/considerations-when-using-the-siebel-adapter-with-sharepoint.md).  
  
6.  créer le projet ; Build réussie du projet, un fichier .dll, CustomWebPart.dll, est généré dans le \< *dossier du projet* \> /bin/Debug dossier.  
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a>Étape 2 : Déployer le composant WebPart personnalisé à un portail SharePoint  
 Vous devez effectuer les opérations suivantes pour rendre le fichier CustomWebPart.dll (composant WebPart personnalisé) qui est créé dans « étape 1 : créer un composant WebPart personnalisée » de cette rubrique utilisable sur le portail SharePoint :  
  
-   **Copiez le fichier CustomWebPart.dll dans le dossier bin du portail SharePoint**: Microsoft Office SharePoint Server crée des portails sous la \< *racine du lecteur*\>: \Inetpub\wwwroot\wss\ VirtualDirectories dossier. Un dossier est créé pour chaque portail et peut être identifié avec le numéro de port. Vous devez copier le fichier CustomWebPart.dll créé dans « étape 1 : créer un composant WebPart personnalisée » de cette rubrique pour le \< *racine du lecteur*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\ < *Numéro_port*\>dossier \bin. Par exemple, si le numéro de port de votre portail SharePoint est 13614, vous devez copier le fichier CustomWebPart.dll à la \< *racine du lecteur*\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin dossier.  
  
    > [!TIP]
    >  Une autre consiste à trouver l’emplacement du dossier de votre portail SharePoint à l’aide de la **Gestionnaire des Services Internet (IIS)** fenêtre (**Démarrer** > **exécuter**  >  **inetmgr**). Recherchez votre portail SharePoint dans le **Gestionnaire des Services Internet (IIS)** fenêtre ([*Nom_Ordinateur*] > Sites Web > [*-nom du portail*]), avec le bouton droit, et puis cliquez sur **propriétés** dans le menu contextuel. Dans la boîte de dialogue Propriétés du portail SharePoint, cliquez sur le **répertoire de base** onglet, puis sélectionnez le **chemin d’accès Local** boîte.  
  
-   **Ajoutez l’entrée de contrôle sécurisé dans le fichier web.config**: étant donné que le fichier CustomWebPart.dll sera utilisé sur des ordinateurs différents et par plusieurs utilisateurs, vous devez déclarer le fichier en tant que « safe ». Pour ce faire, ouvrez le fichier web.config situé dans le dossier portail SharePoint à \< *racine du lecteur*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< numéro_port\>. Sous le `<SafeControls>` section du fichier web.config, ajoutez l’entrée de contrôle sécurisé suivante :  
  
    ```  
    <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
     Enregistrez le fichier web.config et fermez-le.  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a>Étape 3 : Configurer le portail SharePoint pour utiliser le composant WebPart personnalisé  
 Vous devez ajouter le composant WebPart personnalisé pour Microsoft Office SharePoint Server Web Part Gallery, afin que vous puissiez l’utiliser sur votre portail SharePoint. Pour cela :  
  
1.  Démarrez l’Administration centrale de SharePoint 3.0. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.  
  
2.  Dans le volet de navigation gauche, cliquez sur le nom de la Services fournisseur partagés (SSP) à laquelle vous souhaitez ajouter le composant WebPart personnalisé.  
  
3.  Sur le **Administration de Services partagés** page, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.  
  
4.  Sur le **paramètres du Site** , cliquez sur **WebPart** sous le **galeries** colonne.  
  
5.  Sur le **galerie de composants WebPart** page pour ajouter le composant WebPart personnalisé à la galerie, cliquez sur **nouveau**. À ce stade le composant WebPart personnalisé n’est pas disponible dans le **galerie de composants WebPart** page.  
  
6.  Sur le **nouveaux composants WebPart** , recherchez **CustomWebPart** (nom du composant WebPart personnalisé) dans la liste, sélectionnez la case à cocher sur la gauche, puis cliquez sur **compléter la galerie** en haut de la page. Cette opération ajoute le **CustomWebPart** entrée dans le **galerie de composants WebPart** page.  
  
 Vous pouvez maintenant utiliser le composant WebPart personnalisé (**CustomWebPart**) pour créer des composants WebPart dans votre portail SharePoint. Le composant WebPart personnalisé (**CustomWebPart**) s’affiche sous le **divers** section dans le **ajouter des WebParts** page.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser l’adaptateur Siebel avec SharePoint](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)