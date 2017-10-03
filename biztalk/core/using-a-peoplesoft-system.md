---
title: "À l’aide d’un système PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c228ac23-184f-4c08-922b-ba84f5f2c52f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c93e025ddb2ccec4b0088c20837a4f307f40aada
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-peoplesoft-system"></a>Utilisation d'un système PeopleSoft
Le système PeopleSoft est accessible à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur PeopleSoft. Ce dernier fait partie des 8 adaptateurs sectoriels fournis par Microsoft à des fins d'utilisation avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 L'atelier PeopleSoft est divisé en deux parties. Le premier atelier (Atelier 1) permet d'utiliser le système PeopleSoft sans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou produit Microsoft (sauf éventuellement Internet Explorer ou tout autre navigateur). Au cours de cet atelier, vous allez vous connecter au système PeopleSoft pour rechercher et modifier un enregistrement de données.  
  
 Dans le cadre du deuxième atelier (Atelier 2), vous allez créer un projet et une orchestration BizTalk. Une fois l'application créée, vous allez la déployer et l'utiliser pour vous connecter au système PeopleSoft à l'aide de l'adaptateur associé. Celui-ci vous permettra d'accéder aux données via l'application BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures de cet atelier, vous devez disposer d'un navigateur et d'une connexion à Internet, ainsi que d'un compte d'utilisateur sur le système PeopleSoft. Vous devez connaître l'emplacement à partir duquel vous pourrez bénéficier d'un accès Web au système PeopleSoft. Vous n'avez besoin ni de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ni d'autres technologies Microsoft.  
  
## <a name="lab-1---using-a-peoplesoft-system"></a>Atelier 1 : utilisation d’un système PeopleSoft  
 Au cours de cet atelier, vous allez utiliser le système PeopleSoft uniquement. Vous n'aurez besoin d'aucun composant de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous allez tester la connectivité à PeopleSoft pour vous assurer que l'Atelier 2 fonctionne correctement. Pour commencer, vous allez vous connecter au système PeopleSoft via son interface Web qui vous permettra de vous connecter à l'aide d'un navigateur tel qu'Internet Explorer.  
  
## <a name="procedures-for-lab-1---using-a-peoplesoft-system"></a>Atelier 1 : utilisation d'un système PeopleSoft  
  
#### <a name="to-log-on-to-peoplesoft-by-using-a-browser"></a>Pour vous connecter à PeopleSoft à l'aide d'un navigateur  
  
-   Connectez-vous au système PeopleSoft en accédant à la page de connexion à PeopleSoft. Entrez votre **ID utilisateur** et **mot de passe** puis cliquez sur **connexion**.  
  
     ![](../core/media/1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb.gif "1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb")  
  
#### <a name="to-locate-and-modify-peoplesoft-data"></a>Pour rechercher et modifier des données PeopleSoft  
  
1.  Une fois connecté, la page qui s'affiche permet de personnaliser le contenu affiché en modifiant sa mise en forme. Faites défiler vers le bas et développez **définir des finances**, cliquez sur **des définitions communes**, cliquez sur **emplacement**, puis cliquez sur **emplacement** à nouveau. Ceci vous amène à la **emplacement** interface de recherche.  
  
     ![](../core/media/62a89cd4-464c-42fd-91cd-60ceeab5b006.gif "62a89cd4-464c-42fd-91cd-60ceeab5b006")  
  
2.  Pour commencer la recherche, définissez **SetID** à  **=** , définissez **Code de l’emplacement** à **commence par**, entrez **un**, puis cliquez sur **recherche**. Cela permet d’afficher les villes dont le nom commence par A dans le **résultats de la recherche** section de l’interface.  
  
     ![](../core/media/86661144-c666-4d72-9227-9f17df715ba4.gif "86661144-c666-4d72-9227-9f17df715ba4")  
  
3.  Cliquez sur l'un des emplacements pour obtenir les informations associées. Par exemple, dans la figure ci-dessous, l’utilisateur a cliqué sur le **AUS01** lien dans le **Code de l’emplacement** colonne.  
  
4.  Entrez de nouvelles données dans un des champs (tels que les **adresse 2** champ) et cliquez sur **enregistrer** dans le coin inférieur gauche. Les données entrées sont sauvegardées dans un enregistrement.  
  
     ![](../core/media/b6eb137c-c0b0-4906-8fbd-1bc036069fb0.gif "b6eb137c-c0b0-4906-8fbd-1bc036069fb0")  
  
5.  Pour vérifier l'application des modifications, répétez ce processus à partir de l'étape 2, recherchez de nouveau ce même enregistrement, puis observez les modifications qui y ont été apportées.  
  
6.  Dans la partie supérieure droite de la fenêtre, cliquez sur **se déconnecter** mettre fin à votre session de PeopleSoft.  
  
     ![](../core/media/7760b541-5155-453e-a682-4780412f3c13.gif "7760b541-5155-453e-a682-4780412f3c13")  
  
    > [!NOTE]
    >  Les instructions indiquées dans l'atelier suivant vous permettront d'utiliser l'adaptateur PeopleSoft pour extraire les informations de l'enregistrement d'emplacement (AUS01) que vous avez modifié.  
  
## <a name="summary"></a>Résumé  
 Au cours de cet atelier, vous vous êtes connecté au système PeopleSoft via un navigateur. Vous avez ensuite recherché des données, puis manipulé et mis à jour le champ Adresse de l'enregistrement. Une fois les modifications apportées, vous avez consulté les données modifiées dans le navigateur pour vérifier que les modifications ont été prises en compte.