---
title: "Envoyer des IDOC à partir d’un système SAP à utiliser l’adaptateur mySAP dans BizTalk | Documents Microsoft"
description: 
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aea8a5e9-d775-4d52-a434-c2908b53cd2d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63f7d1ccdaa8cb6a4ee12ad1cc4263c487a164c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-idocs-from-an-sap-system"></a>Envoyer des IDOC à partir d’un système SAP
Tâches principales à effectuer sur le système SAP pour envoyer un IDOC à partir du système SAP à une application externe. Contactez votre administrateur SAP pour effectuer ces tâches, ou reportez-vous à l’aide de SAP.  
  
## <a name="send-an-idoc-from-sap"></a>Envoyer un IDOC de SAP  
  
1.  Démarrez l’interface utilisateur graphique SAP.  
  
2.  Créer un système logique à l’aide de la transaction de BD54.  
  
3.  Créer une destination RFC dans les connexions TCP/IP à l’aide de la transaction de SM59.  
  
4.  Créer un port à l’aide de la transaction de WE21 et l’attacher à la destination RFC créée dans la dernière étape.  
  
5.  Créer un profil de partenaire à l’aide de la transaction de WE20 avec le type de message requis et IDOC, puis l’attacher au port créé dans la dernière étape.  
  
6.  Mettre à jour un modèle distribué en vous connectant le type de message pour le port à l’aide de la transaction de vente.  
  
7.  Générer un IDOC dans SAP. Par exemple, utiliser les transactions BD10 pour déclencher un IDOC MATMAS. Pour plus d’informations sur les autres transactions pour déclencher des IDOC spécifiques, contactez votre administrateur SAP.  

## <a name="view-transaction-ids-in-sap"></a>Affichage des ID de Transaction dans SAP
Lorsque le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] appelle un tRFC ou envoie un IDOC à un système SAP, les registres de système SAP une transaction ID (TID) en réponse. Dans certains scénarios, vous devez connaître le TID est inscrit avec le système SAP en réponse à un appel à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Par exemple, vous souhaiterez identifier l’unité logique de travail (LUW) sur le système SAP pour résoudre un problème.  
  
 Pour afficher le TID dans un système SAP, vous devez utiliser des transactions SM58. Contactez votre administrateur SAP ou consultez le Guide de SAP pour plus d’informations sur cette transaction. 

## <a name="view-details-about-idocs-sent-and-received-from-sap"></a>Afficher les détails des IDOC envoyés et reçus à partir de SAP
À l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous pouvez envoyer un IDOC à un système SAP ou un IDOC de réception à partir d’un système SAP. Pour suivre l’état et afficher les données d’un IDOC envoyé ou reçu par un système SAP, vous pouvez utiliser la transaction WE02. Contactez votre administrateur SAP, ou consultez les conseils de SAP pour plus d’informations sur cette transaction.  

  
## <a name="see-also"></a>Voir aussi  
 [Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)