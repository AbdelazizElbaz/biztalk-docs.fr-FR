---
title: "Comment créer un Port1 envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: bf32e9f5-ebed-43d2-b9a9-6ab91925d973
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf49b16da34c5341059db34d6874b7099ab54df6
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-a-send-port"></a>Comment créer un Port d’envoi
La procédure suivante permet de créer des ports d'envoi BizTalk Server pour JD Edwards EnterpriseOne.  
  
### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Cliquez avec le bouton droit sur le nœud Ports d'envoi.  
  
2.  Cliquez sur **ajouter le Port d’envoi**.  
  
3.  Dans le **créer un Port d’envoi** boîte de dialogue, sélectionnez **Port statique avec sollicitation-réponse** à partir de la **spécifier le type de Port d’envoi** liste, puis cliquez sur **OK**.  
  
     Le **statique propriétés du Port d’envoi avec sollicitation-réponse** fenêtre s’ouvre.  
  
4.  Tapez un nom pour le port d’envoi, par exemple, `SSOSendToJDEEntOne`.  
  
5.  Cliquez sur **Transport** dans le volet gauche.  
  
6.  Cliquez sur **Type de Transport**, puis sélectionnez **JDEEntOne**.  
  
7.  Sélectionnez le **adresse (URI)**, puis cliquez sur le bouton de sélection (...).  
  
     JD Edwards EnterpriseOne **propriétés du Transport** boîte de dialogue s’affiche.  
  
8.  Type `myJDEEntOneSSO` pour le **nom système logique**.  
  
9. Sélectionnez **Oui** pour **utiliser l’authentification unique**.  
  
10. Dans la liste déroulante, sélectionnez l'application associée à authentification unique que vous avez créée pour représenter le système JD Edwards EnterpriseOne.  
  
     Cliquez sur **OK** pour confirmer les informations que vous avez entré.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’Applications associées](../core/creating-affiliate-applications4.md)   
 [Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)