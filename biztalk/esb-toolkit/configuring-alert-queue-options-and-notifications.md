---
title: "Configuration des Options d’alerte de file d’attente et des Notifications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f78afbf9-6e27-4887-8424-f265fbd8448a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914af88b989c73444e16acedf43b9a236897859d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-alert-queue-options-and-notifications"></a>Configuration des Notifications et des Options d’alerte de file d’attente
Le portail de gestion ESB utilise le Service d’alerte ESB pour générer des alertes comme messages d’erreur arrivent sur le portail et elle utilise le Service de Notification ESB à la file d’attente et envoyer des notifications aux utilisateurs qui s’abonnent aux alertes. Vous pouvez modifier les paramètres utilisés par ces services dans le portail de gestion ESB.  
  
### <a name="to-configure-the-settings-for-the-esb-alert-service"></a>Pour configurer les paramètres pour le Service d’alerte ESB  
  
1.  Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de Microsoft BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).  
  
2.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).  
  
3.  Dans le **Options d’alerte pour file d’attente** section, activez ou désactivez le **activer le Service de file d’attente alerte** case à cocher pour activer ou désactiver le service.  
  
4.  Si vous activez le service, modifiez les valeurs dans les autres contrôles pour répondre à nos besoins. Le service interagit avec Microsoft Active Directory, vous devez spécifier la chaîne de connexion LDAP (Lightweight Directory Access Protocol) appropriée. Vous pouvez également spécifier la taille de lot de file d’attente et l’intervalle d’interrogation.  
  
5.  Cliquez sur **enregistrer** pour enregistrer les nouveaux paramètres.  
  
### <a name="to-configure-the-settings-for-the-esb-alert-email-notification-service"></a>Pour configurer les paramètres pour le service de Notification des alertes par courrier électronique pour ESB  
  
1.  Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).  
  
2.  Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).  
  
3.  Dans le **Options d’alerte par courrier électronique** section, activez ou désactivez le **activer le Service de messagerie alerte** case à cocher pour activer ou désactiver le service.  
  
4.  Si vous activez le service, modifiez les valeurs dans les autres contrôles pour répondre à nos besoins. Spécifiez le nom de serveur de messagerie et l’adresse « de », modifier la taille d’intervalle et le lot d’interrogation en fonction des besoins et spécifiez le chemin d’accès aux fichiers de langue Transformations XSLT (Extensible Stylesheet) utilisé par le service.  
  
5.  Cliquez sur **enregistrer** pour enregistrer les nouveaux paramètres.