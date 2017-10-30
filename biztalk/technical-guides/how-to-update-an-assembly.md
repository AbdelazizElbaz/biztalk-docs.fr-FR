---
title: "Comment mettre à jour un Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f456c8f-247a-4d5c-b5af-41e88968779c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163b06706652b1f65b9a76e3feea8911a2ca4c88
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-an-assembly"></a>Comment mettre à jour un Assembly
Cette rubrique décrit comment mettre à jour la version d’un assembly et l’application qu’un assembly est déployé à l’aide de Visual Studio 2010.  
  
> [!NOTE]  
>  Si vous mettez à jour un assembly avec une version plus récente, il n'est pas nécessaire de redémarrer l'application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="updating-an-assembly"></a>Mise à jour d’un Assembly  
  
#### <a name="to-increment-the-version-number-of-an-assembly"></a>Pour incrémenter le numéro de version d’un assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur le **Application** onglet.  
  
3.  Dans le volet droit, cliquez sur **informations de l’Assembly**.  
  
4.  Dans le **informations d’Assembly** boîte de dialogue, spécifiez les valeurs pour le **Version de l’Assembly** champ pour augmenter le numéro de version d’assembly. Vous ne devez augmenter que le numéro de version majeure ou mineure. Le numéro de version majeure est le premier chiffre de la séquence (***n***.0.0.0).) ; le numéro de version mineure est le deuxième chiffre de la séquence (0. ***n*** . 0.0). BizTalk Server ne reconnaît pas une modification de numéro de version plus loin dans la séquence, telles que 0.0.  ***n*** .0 ou 0.0.0. ***n***.  
  
5.  Cliquez sur **OK** pour fermer la **informations d’Assembly** boîte de dialogue.  
  
6.  Enregistrez le projet.  
  
    > [!NOTE]  
    >  Utilisez le Concepteur de pipeline et le Modèle objet de l'Explorateur BizTalk pour éviter tout conflit de schémas lors de l'incrémentation des versions d'assembly.  
  
#### <a name="to-change-the-application-that-an-assembly-is-deployed-to"></a>Pour modifier l’application déployée dans un assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur le **déploiement** onglet.  
  
3.  Dans le volet droit, spécifiez le nom de l’application dans le **nom de l’Application** champ.  
  
4.  Vérifiez que le **installer dans le Global Assembly Cache** est définie sur **True**.  
  
    > [!NOTE]  
    >  Lorsque vous déployez la solution, les assemblys sont déployés dans la nouvelle application et installés dans le GAC.