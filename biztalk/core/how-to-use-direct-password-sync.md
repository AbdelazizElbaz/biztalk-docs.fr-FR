---
title: Comment utiliser la synchronisation de mot de passe directe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1334c2f-2020-46ea-a98c-f7688813e38c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6080589271d845432e875cb335a2ef354c9784ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-direct-password-sync"></a>Utilisation de la synchronisation de mot de passe directe
Cette version de l'authentification unique de l'entreprise inclut la fonctionnalité Synchronisation de mot de passe directe à partir de Windows. Celle-ci vous évite de créer un adaptateur de synchronisation de mot de passe et met à jour le mot de passe, directement depuis Windows, dans la base de données SSO.  
  
 La synchronisation de mot de passe directe à partir de Windows est utile dans les situations suivantes :  
  
-   Le système de votre entreprise nécessite un mappage entre deux comptes Windows.  
  
-   Vous devez mettre à jour le mot de passe de l'utilisateur externe dans la base de données SSO directement lorsque le mot de passe de l'utilisateur Windows est modifié. Vous pouvez modifier le mot de passe sur le système principal (qui correspond à l'utilisateur externe) à l'aide d'autres mécanismes. Par exemple, vous pouvez utiliser MIIS (Microsoft Identity Integration Server) pour mettre à jour les mots de passe dans RACF (Resource Access Control Facility) sur un macroordinateur IBM à l'aide de RACF Management Agent.  
  
### <a name="to-enable-direct-password-sync"></a>Pour activer la synchronisation de mot de passe directe  
  
1.  Ouvrez l'authentification unique de l'entreprise.  
  
2.  Dans le volet d’étendue, cliquez sur **Applications associées**.  
  
3.  Avec le bouton droit approprié **Application associée**.  
  
4.  Cliquez sur **Propriétés**.  
  
     Le **propriétés des Applications associées** boîte de dialogue s’affiche.  
  
5.  Cliquez sur le **Options** onglet.  
  
6.  Sélectionnez le **synchronisation de mot de passe directe à partir de Windows** case à cocher.  
  
7.  Cliquez sur **OK**.