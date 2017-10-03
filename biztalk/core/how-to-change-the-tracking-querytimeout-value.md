---
title: Comment modifier la valeur QueryTimeout du suivi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [HAT], time-out limits
- HAT, time-out limits
ms.assetid: abc26f37-6537-42fa-81ff-bc8b758b4e10
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca9f61466323e0b154bdeb0499cc5cee6e4ef10c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-tracking-querytimeout-value"></a>Modification de la valeur QueryTimeout du suivi
Par défaut, le suivi des messages et des instances de service expire si une requête s'exécute pendant plus de 60 secondes. Vous pouvez modifier cette valeur dans le registre afin que les requêtes puissent s'exécuter pendant plus de 60 secondes.  
  
> [!CAUTION]
>  Une modification incorrecte du Registre peut sérieusement endommager votre système. Avant d'apporter des modifications au Registre, il convient de sauvegarder les données importantes qui se trouvent sur l'ordinateur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
### <a name="to-change-the-query-timeout-value"></a>Pour modifier la valeur du délai de la requête  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.  
  
2.  Dans l'Éditeur du Registre, recherchez la sous-clé suivante, puis cliquez dessus :  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3. 0**  
  
3.  S'il existe une sous-clé de suivi, passez à l'étape 6.  
  
4.  Pour créer une sous-clé de suivi sur le **modifier** menu, pointez sur **nouveau**, puis cliquez sur **clé**.  
  
5.  Type **suivi**, puis appuyez sur ENTRÉE.  
  
6.  Recherchez la sous-clé suivante, puis cliquez dessus :  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**  
  
7.  Sur le **modifier** menu, pointez sur **nouveau**, puis cliquez sur **valeur DWORD**.  
  
8.  Type **ConnectionTimeout**, puis appuyez sur ENTRÉE.  
  
9. Avec le bouton droit **ConnectionTimeout**, puis cliquez sur **modifier**.  
  
10. Dans le **modifier la valeur DWORD** boîte de dialogue, cliquez sur **décimal**.  
  
11. Dans le **données de la valeur** zone, tapez la valeur en secondes pendant laquelle vous souhaitez définir pour la valeur de délai d’attente de requête, puis cliquez sur **OK**.  
  
12. Dans le menu **Fichier** , cliquez sur **Quitter**.  
  
    > [!NOTE]
    >  Il se peut que vous deviez fermer, puis rouvrir la console Administration de BizTalk Server pour que la nouvelle valeur soit prise en compte.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données historiques et de suivi](../core/viewing-historical-and-tracked-data.md)