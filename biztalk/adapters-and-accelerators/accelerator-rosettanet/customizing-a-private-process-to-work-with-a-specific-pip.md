---
title: "Personnalisation d’un processus privé pour travailler avec une adresse PIP spécifique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, PIPs
- private processes, customizing
- developing, private processes
- PIPs, private processes
- customizing private processes
ms.assetid: 88494e87-25a0-4c94-9396-61a0e07964aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec579716f9ab02389ce9f2d5ae5ec02ef0b30730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-a-private-process-to-work-with-a-specific-pip"></a>Personnalisation d’un processus privé pour travailler avec une adresse PIP spécifique
Vous pouvez créer une expression de filtre qui provoque un répondeur orchestration de processus privé pour traiter ou pas les instances de processus de des processus PIP (Partner Interface). Cela vous donne la souplesse de création d’un processus personnalisé privé pour recevoir et traiter certaines instances PIP et d’utilisation des processus privé par défaut toutes les autres instances PIP.  
  
 Pour créer un processus personnalisé privé pour travailler avec un spécifique PIP ou plusieurs PIP spécifique, vous créez une expression de filtre pour la forme réception de l’orchestration de processus privé. Par exemple, l’orchestration PIP3A4PrivateResponder.odx dans les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel. Il se trouve à \< *lecteur*> : \Program Files\BizTalk \<version > Accelerator for RosettaNet\SDK\PIP3A4Process à l’aide de Business Rules\PIP3A4PrivateResponder.  
  
 En plus de créer un processus privé qui traitent uniquement des instances d’un PIP spécifique, vous devez personnaliser le processus privé de BTARN par défaut afin qu’il ne traitera pas les instances pour ce PIP.  
  
### <a name="to-customize-a-responder-private-process-to-work-with-a-specific-pip"></a>Pour personnaliser un processus privé répondeur pour travailler avec une adresse PIP spécifique  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], créez une orchestration de processus privé répondeur personnalisés pour travailler avec une adresse PIP spécifique. Vous pouvez baser l’orchestration sur l’orchestration de processus privé par défaut BTARN répondeur.  
  
    > [!NOTE]
    >  Vous pouvez trouver la valeur par défaut orchestration de processus privé de répondeur, nommée PrivateResponder.odx, dans le SDK de BTARN. Il se trouve à  *\<lecteur >*: \Program Files\BizTalk \<version > Accelerator for RosettaNet\SDK\PrivateResponder.  
  
2.  Ajouter une orchestration personnalisée à votre projet BizTalk. Assurez-vous que votre projet contient une référence au fichier Microsoft.Solutions.BTARN.GlobalSchemas.dll.  
  
3.  Ouvrez l’orchestration personnalisée dans le Concepteur d’Orchestration.  
  
4.  Avec le bouton droit de la première **réception** forme qui active l’orchestration, puis cliquez sur **modifier l’Expression de filtre**.  
  
    > [!NOTE]
    >  La forme réception pour l’orchestration de processus privé par défaut BTARN répondeur a deux conditions de filtre : Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == « AsyncAction » ou Microsoft.Solutions.BTARN.GlobalSchemas.SCCategory == « SyncAction ». Cette expression permet de s’assurer que l’orchestration traite les messages RosettaNet. Conserver cette expression de filtre dans une orchestration personnalisée.  
  
5.  Dans le **Expression de filtre** boîte de dialogue, dans la colonne de propriété dans la première ligne ouvrir, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante, dans la colonne d’opérateur Sélectionnez  **==**  dans la liste déroulante, dans la colonne valeur, tapez le code PIP à trois chiffres, par exemple, tapez **3 a 4**.  
  
6.  Cliquez sur **OK**.  
  
7.  Ouvrez le projet d’orchestration de processus privé par défaut répondeur (PrivateResponder.btproj) dans le Concepteur d’Orchestration. Assurez-vous que le projet contient une référence de travail dans le fichier Microsoft.Solutions.BTARN.GlobalSchemas.dll.  
  
8.  Double-cliquez sur **PrivateResponder.odx**.  
  
9. Cliquez sur le **ReceiveFromPublicProcessResponder** forme réception, puis cliquez sur **modifier l’Expression de filtre**.  
  
10. Dans le **Expression de filtre** boîte de dialogue, dans la colonne de propriété dans la première ligne ouvrir, sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante. Dans la colonne d’opérateur, sélectionnez **! =** dans la liste déroulante. Dans la colonne valeur, tapez le code PIP à trois chiffres, par exemple, tapez «**3 a 4 »**.  
  
11. Cliquez sur **OK**.  
  
12. Dans l’Explorateur de solutions, cliquez sur le projet qui contient l’orchestration, puis **Build**.  
  
13. Une fois que le projet a été généré avec succès, cliquez sur le projet, puis cliquez sur **déployer**.  
  
14. Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
15. Déplacer vers \< *lecteur*> : \Program Files\BizTalk \<version > Accelerator for RosettaNet\SDK\PrivateResponder, sélectionnez **PrivateResponder.odx**, puis cliquez sur  **OK**.  
  
16. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis cliquez sur **Générer**.  
  
17. Une fois que le projet a été généré avec succès, cliquez sur le projet, puis cliquez sur **déployer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)