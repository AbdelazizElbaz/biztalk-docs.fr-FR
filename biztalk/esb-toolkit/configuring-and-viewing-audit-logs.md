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
# <a name="configuring-and-viewing-audit-logs"></a><span data-ttu-id="7b11e-102">Configuration et l’affichage des journaux d’Audit</span><span class="sxs-lookup"><span data-stu-id="7b11e-102">Configuring and Viewing Audit Logs</span></span>
<span data-ttu-id="7b11e-103">Le portail de gestion ESB conserve un journal d’audit des actions qui vous aident à surveiller l’utilisation et le suivi des problèmes.</span><span class="sxs-lookup"><span data-stu-id="7b11e-103">The ESB Management Portal maintains an audit log of actions that help you to monitor usage and track problems.</span></span> <span data-ttu-id="7b11e-104">Les administrateurs peuvent spécifier les événements que le portail écrit dans le journal d’audit.</span><span class="sxs-lookup"><span data-stu-id="7b11e-104">Administrators can specify which events the portal will write to the audit log.</span></span>  
  
### <a name="to-view-the-audit-logs-for-the-portal"></a><span data-ttu-id="7b11e-105">Pour afficher les journaux d’audit pour le portail</span><span class="sxs-lookup"><span data-stu-id="7b11e-105">To view the audit logs for the portal</span></span>  
  
1.  <span data-ttu-id="7b11e-106">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **gérer le journal d’Audit** pour ouvrir le [Page du journal d’Audit](../esb-toolkit/audit-log-page.md).</span><span class="sxs-lookup"><span data-stu-id="7b11e-106">Point to the **Admin** tab on the portal main menu, and then click **Manage Audit Log** to open the [Audit Log Page](../esb-toolkit/audit-log-page.md).</span></span>  
  
2.  <span data-ttu-id="7b11e-107">Pour afficher les détails de la nouvelle soumission et le message d’origine pour les messages soumise à nouveau, cliquez sur l’identificateur d’un message dans la liste pour ouvrir le journal d’Audit – page de l’Afficheur des messages.</span><span class="sxs-lookup"><span data-stu-id="7b11e-107">To see the resubmission details and the original message for resubmitted messages, click the identifier of a message in the list to open the Audit Log – Message Viewer page.</span></span>  
  
### <a name="to-configure-the-auditing-settings-for-the-portal"></a><span data-ttu-id="7b11e-108">Pour configurer les paramètres d’audit pour le portail</span><span class="sxs-lookup"><span data-stu-id="7b11e-108">To configure the auditing settings for the portal</span></span>  
  
1.  <span data-ttu-id="7b11e-109">Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).</span><span class="sxs-lookup"><span data-stu-id="7b11e-109">Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="7b11e-110">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="7b11e-110">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="7b11e-111">Pour modifier les options d’audit, sélectionnez les cases à cocher dans la **AuditOptions** section pour chaque événement que vous souhaitez auditer.</span><span class="sxs-lookup"><span data-stu-id="7b11e-111">To change the auditing options, select the check boxes in the **AuditOptions** section for each event you want to audit.</span></span> <span data-ttu-id="7b11e-112">Les événements disponibles sont l’enregistrement des paramètres modifiés, renvoyés réussie d’une erreur après avoir modifié et Échec lors de la soumettre à nouveau une erreur.</span><span class="sxs-lookup"><span data-stu-id="7b11e-112">The available events are the saving of modified settings, successful resubmission of a fault after editing, and failure when resubmitting a fault.</span></span>