---
title: "À l’aide d’un système JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5346aa04-ebd7-4545-9062-b349fd73b7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 835432e50bce3f347e6f769fb8182ab35fc4f949
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-jd-edwards-oneworld-system"></a>Utilisation d'un système JD Edwards OneWorld
Le système JD Edwards OneWorld est accessible à partir d'un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur JD Edwards OneWorld. Ce dernier fait partie des 8 adaptateurs sectoriels fournis par Microsoft à des fins d'utilisation avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 L'atelier JD Edwards OneWorld est divisé en deux parties. Le premier atelier (Atelier 1) vous permet d'utiliser le système JD Edwards OneWorld sans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou produit Microsoft. Vous allez utiliser l'outil client JD Edwards OneWorld pour vous connecter à une base de données JD Edwards OneWorld et localiser un enregistrement spécifique sur la base de l'adresse.  
  
 Dans le cadre du deuxième atelier (Atelier 2), vous allez créer un projet et une orchestration BizTalk. Une fois l'application créée, vous allez la déployer et l'utiliser pour vous connecter au système JD Edwards OneWorld à l'aide de l'adaptateur associé. Celui-ci vous permettra d'accéder aux données via l'application BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures de cet atelier, vous devez installer le logiciel client JD Edwards OneWorld ainsi que sa dernière mise à jour. Pour utiliser les outils du logiciel client, vous avez besoin d'une base de données JD Edwards OneWorld, d'une connectivité réseau à celle-ci et d'un compte utilisateur sur ce système. Vous n'avez pas besoin de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour réaliser cet atelier.  
  
## <a name="lab-1---using-a-jd-edwards-oneworld-system"></a>Atelier 1 : utilisation d'un système JD Edwards OneWorld  
 Au cours de cet atelier, vous allez utiliser le système JD Edwards OneWorld uniquement. Vous n'aurez besoin d'aucun composant de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous allez tester la connectivité à JD Edwards OneWorld pour vous assurer que l'atelier 2 fonctionne correctement. Vous allez utiliser l'outil SQL Plus pour JD Edwards OneWorld afin de créer et manipuler une table de données dans une base de données JD Edwards OneWorld.  
  
## <a name="procedures-for-lab-1---using-a-jd-edwards-oneworld-system"></a>Atelier 1 : utilisation d’un système JD Edwards OneWorld  
  
#### <a name="to-log-on-to-jd-edwards-oneworld-by-using-a-browser"></a>Pour se connecter à JD Edwards OneWorld à l'aide d'un navigateur  
  
-   Connectez-vous au système JD Edwards OneWorld en cliquant sur l'icône JD Edwards OneWorld. Entrez votre **ID utilisateur**, **mot de passe**, et **environnement**, puis cliquez sur **OK**.  
  
     ![](../core/media/f04db2ef-d587-4357-b9e8-c96319886e97.gif "f04db2ef-d587-4357-b9e8-c96319886e97")  
  
#### <a name="to-locate-and-view-jd-edwards-oneworld-data"></a>Pour rechercher et afficher des données JD Edwards OneWorld  
  
1.  Une fois connecté à la **Explorateur JD Edwards OneWorld**.  
  
     ![](../core/media/14e8c206-7e38-48f8-9108-e32a7ac9a740.gif "14e8c206-7e38-48f8-9108-e32a7ac9a740")  
  
2.  Développez **répertoire principal**, puis **Foundation Systems**, puis **carnet d’adresses**, puis **traitement tous les jours**.  
  
     ![](../core/media/1f742221-00e5-4697-95ff-64aa63ed567a.gif "1f742221-00e5-4697-95ff-64aa63ed567a")  
  
3.  Dans la fenêtre de droite, double-cliquez sur **Address Book Revisions**.  
  
     ![](../core/media/a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031.gif "a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031")  
  
4.  Pour **Alpha Name**, entrez `Ga`, sélectionnez le **affichage adresse** case à cocher, puis cliquez sur **trouver** dans la barre d’outils.  
  
     ![](../core/media/2f58413f-41a9-4ed9-ba5c-1d6d59eafb01.gif "2f58413f-41a9-4ed9-ba5c-1d6d59eafb01")  
  
     Dans le **Address Book Revisions - [Work With Addresses]** boîte de dialogue, deux enregistrements sont affichés à la suite de la recherche.  
  
     ![](../core/media/9284df4e-ca9b-48ab-b2bf-a90d765d4a05.gif "9284df4e-ca9b-48ab-b2bf-a90d765d4a05")  
  
     Une autre méthode de localisation des données consiste à effacer le **Alpha Name** , cliquez sur dans la zone de texte ci-dessus le **numéro d’adresse** colonne, puis entrez `500`. Cliquez sur **trouver** dans la barre d’outils pour afficher les résultats de recherche.  
  
     ![](../core/media/a88bd867-9a16-416a-a43e-cdfcc65fc670.gif "a88bd867-9a16-416a-a43e-cdfcc65fc670")  
  
     Dans l’atelier 2, il y a des instructions pour l’utilisation de l’adaptateur JD Edwards OneWorld pour extraire les informations d’un **numéro d’adresse** de `500`.  
  
5.  Sur le **fichier** menu, cliquez sur **quitter** pour quitter la session Client JD Edwards OneWorld.  
  
## <a name="summary"></a>Résumé  
 Dans cet atelier, vous avez utilisé l'outil client JD Edwards OneWorld pour vous connecter au système JD Edwards OneWorld. Après avoir établi la connexion, vous avez recherché des données spécifiques et vous avez affiché les enregistrements de données renvoyés.