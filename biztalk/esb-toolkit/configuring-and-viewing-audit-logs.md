---
title: "Configuration et l’affichage des journaux d’Audit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c725bf04-d59f-42c1-b327-b4268421689c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c88e0a67a393b7ddc35ee8865d99d0299d41f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-and-viewing-audit-logs"></a>Configuration et l’affichage des journaux d’Audit
Le portail de gestion ESB conserve un journal d’audit des actions qui vous aident à surveiller l’utilisation et le suivi des problèmes. Les administrateurs peuvent spécifier les événements que le portail écrit dans le journal d’audit.  
  
### <a name="to-view-the-audit-logs-for-the-portal"></a>Pour afficher les journaux d’audit pour le portail  
  
1.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **gérer le journal d’Audit** pour ouvrir le [Page du journal d’Audit](../esb-toolkit/audit-log-page.md).  
  
2.  Pour afficher les détails de la nouvelle soumission et le message d’origine pour les messages soumise à nouveau, cliquez sur l’identificateur d’un message dans la liste pour ouvrir le journal d’Audit – page de l’Afficheur des messages.  
  
### <a name="to-configure-the-auditing-settings-for-the-portal"></a>Pour configurer les paramètres d’audit pour le portail  
  
1.  Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).  
  
2.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).  
  
3.  Pour modifier les options d’audit, sélectionnez les cases à cocher dans la **AuditOptions** section pour chaque événement que vous souhaitez auditer. Les événements disponibles sont l’enregistrement des paramètres modifiés, renvoyés réussie d’une erreur après avoir modifié et Échec lors de la soumettre à nouveau une erreur.