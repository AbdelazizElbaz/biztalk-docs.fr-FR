---
title: "Travaillez dans le Concepteur d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06742cb8-f6d6-46e2-adc0-6be9a3d6a447
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf474c68d91b7648f7f0efcfe4e85e7531e4aa1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="working-in-itinerary-designer"></a>Vous travaillez dans le Concepteur d’itinéraire
Après avoir créé un projet Microsoft Visual c#, vous pouvez créer de nouveaux modèles d’itinéraire et ajouter des itinéraires existants au projet. Les étapes suivantes décrivent comment créer une nouvelle feuille de route, ajouter un modèle d’itinéraire existant ou modifier le nom d’un itinéraire.  
  
> [!NOTE]
>  Avant d’utiliser le Concepteur d’itinéraire, vous devez installer le programme d’installation de Windows Microsoft.Practices.ESB.CORE (fichier .msi) à partir de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] le dossier d’installation. Cette étape installe les assemblys d’exécution requis dans le global assembly cache.  
  
## <a name="basic-operations"></a>Opérations de base  

#### <a name="create-an-itinerary"></a>Créer un itinéraire  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nom du projet c#, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
2.  Dans le **nom** zone située au bas de la boîte de dialogue, tapez le nom de l’itinéraire, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  La nouvelle feuille de route est créé et affiché dans le Concepteur d’itinéraire et un fichier .itinerary correspondant est créé et affiché dans l’Explorateur de solutions.  
  
#### <a name="add-an-existing-itinerary-to-the-project"></a>Ajoutez un itinéraire existant au projet
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet c#, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
2.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au répertoire qui contient la feuille de route, cliquez sur l’itinéraire, puis cliquez sur **ajouter**.  
  
    > [!NOTE]
    >  L’itinéraire est ajouté au projet.  
  
#### <a name="change-the-name-of-an-itinerary"></a>Modifier le nom d’un itinéraire  
  
1.  Dans l’Explorateur de solutions, cliquez sur le fichier .itinerary que vous souhaitez renommer, puis cliquez sur **renommer**.  
  
2.  Tapez le nouveau nom de fichier, puis appuyez sur ENTRÉE.  
  
#### <a name="save-an-itinerary"></a>Enregistrer un itinéraire  
  
Sur le **fichier** menu, cliquez sur **enregistrer \<nom d’itinéraire\>**.  
  
> [!NOTE]
>  Fichiers d’itinéraire sont enregistrés en tant que modèles DSL format XML correspondant.  
  
#### <a name="set-itinerary-export-properties"></a>Définir les propriétés de l’exportation d’itinéraire  
  
1.  Dans la fenêtre Propriétés, tapez un **nom** propriété.  
  
2.  Dans la fenêtre Propriétés, tapez un **Version** propriété.  
  
3.  Dans la fenêtre Propriétés, définissez la **réponse à la demande est** propriété à l’aide de la liste déroulante. Définissez cette propriété sur **true** si le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] application cliente communique avec une rampe d’entrée à l’aide du modèle d’échange de messages de demande-réponse.  
  
4.  Dans la fenêtre Propriétés, définissez la **exporter un Mode** propriété **par défaut** ou **Strict**.  
  
    > [!NOTE]
    >  Lors de la création [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinéraires à l’aide du Concepteur d’itinéraire, le **exporter un Mode** propriété peut être utilisée pour définir où le service s’exécute. Définition de la **exporter un Mode** propriété **Strict** garantit que l’itinéraire service s’exécute dans son conteneur prescrite ; dans ce cas, chaque service d’itinéraire dans l’itinéraire XML a une propriété de l’étape qui Spécifie le pipeline dans laquelle le service s’exécute. Si cette propriété est définie sur **par défaut**, un itinéraire compatible avec Microsoft ESB est créé, avec aucune phase spécifié, et le service d’itinéraire s’exécute dans l’ordre indiqué, mais pas nécessairement dans l’étape de pipeline que vous le souhaitez.  
  
#### <a name="export-an-itinerary-to-a-file"></a>Exporter un itinéraire vers un fichier  
  
1.  Dans la fenêtre Propriétés, cliquez sur **XML itinéraire exportateur** dans les **modèle exportateur** liste déroulante.  
  
2.  Dans la fenêtre Propriétés, définissez la **fichier XML de la feuille de route** à une nouvelle valeur de propriété.  
  
#### <a name="export-an-itinerary-to-a-database"></a>Exporter un itinéraire pour une base de données  
  
1.  Dans la fenêtre Propriétés, cliquez sur **exportateur de feuille de route de base de données** dans les **modèle exportateur** liste déroulante.  
  
2.  Dans la fenêtre Propriétés, définissez la **base de données de la feuille de route** chaîne de connexion de propriété pour pointer vers la base de données d’itinéraire.  
  
3.  Dans la fenêtre Propriétés, définissez la **état de la feuille de route** propriété **publié** ou **déployées**.  
  
    > [!NOTE]
    >  Lorsqu’un itinéraire est exporté vers une base de données avec **état de la feuille de route** la valeur **publié**, l’itinéraire se ne pas effet pour la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exécution jusqu'à ce que lorsque la propriété est définie à  **Déployé**.  
  
## <a name="security-operations"></a>Opérations de sécurité  
 À l’aide du Concepteur d’itinéraire, vous pouvez protéger des informations sensibles, telles que les mots de passe et autres informations d’identification stockées dans un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] d’itinéraire, en chiffrant ces informations à l’aide de certificats X.509.  
  
#### <a name="select-the-x509-certificate-for-an-itinerary"></a>Sélectionnez le certificat X.509 pour un itinéraire  
  
1.  Dans la fenêtre Propriétés de concepteur d’itinéraire, développez le **le certificat de chiffrement** propriété, puis cliquez sur le **magasin** liste déroulante, puis sélectionnez le **CurrentUser**ou **LocalMachine**. Cela associe le magasin de certificats X.509 à l’utilisateur actuel ou l’ordinateur local.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **nom du magasin** liste déroulante et sélectionnez la valeur qui correspond à votre magasin de certificats.  
  
3.  Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (...) en regard de la propriété du certificat de chiffrement, puis sélectionnez le **certificat X.509** dans les **sélectionner un certificat** boîte de dialogue.  
  
#### <a name="remove-the-x509-certificate-from-an-itinerary"></a>Supprimer le certificat X.509 à partir d’un itinéraire  
  
-   Dans la fenêtre Propriétés de concepteur d’itinéraire, développez le **le certificat de chiffrement** propriété et définissez la **magasin** propriété sur une autre valeur. Il dissocie l’ancien certificat avec la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] modèle d’itinéraire.  
  
#### <a name="disable-the-x509-certificate-validation"></a>Désactiver la validation du certificat X.509  
  
Dans l’Éditeur du Registre, accédez à la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**, puis définissez le **RequireX509Certificate** valeur de propriété  **false**.  
  
> [!NOTE]
>  Si vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] sur un système d’exploitation qui prend en charge 64 bits, la sous-clé est **HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**.