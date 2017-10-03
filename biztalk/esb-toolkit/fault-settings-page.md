---
title: "Page Paramètres d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67f10b8b-9a32-40ca-9ce4-0b69e159c36c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5ce03e5284122e8c1de9bd4e5c2d69c392174e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fault-settings-page"></a><span data-ttu-id="4a2d5-102">Page Paramètres des erreurs</span><span class="sxs-lookup"><span data-stu-id="4a2d5-102">Fault Settings Page</span></span>
<span data-ttu-id="4a2d5-103">Figure 1 montre la page Paramètres de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-103">Figure 1 shows the Fault Settings page.</span></span> <span data-ttu-id="4a2d5-104">Cette page affiche une plage de paramètres d’administration que vous pouvez modifier.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-104">This page displays a range of administrative settings that you can modify.</span></span>  
  
 <span data-ttu-id="4a2d5-105">![Page Paramètres d’erreur](../esb-toolkit/media/ch8-faultsettingspage.gif "Ch8-FaultSettingsPage")</span><span class="sxs-lookup"><span data-stu-id="4a2d5-105">![Fault Settings Page](../esb-toolkit/media/ch8-faultsettingspage.gif "Ch8-FaultSettingsPage")</span></span>  
  
 <span data-ttu-id="4a2d5-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="4a2d5-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="4a2d5-107">**La page Paramètres de pannes du portail de gestion ESB**</span><span class="sxs-lookup"><span data-stu-id="4a2d5-107">**The ESB Management Portal Fault Settings page**</span></span>  
  
 <span data-ttu-id="4a2d5-108">La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page Paramètres de pannes du portail de gestion ESB :</span><span class="sxs-lookup"><span data-stu-id="4a2d5-108">The following list explains how you can use the features of the ESB Management Portal Fault Settings page:</span></span>  
  
-   <span data-ttu-id="4a2d5-109">Pour modifier les options d’audit, sélectionnez les cases à cocher pour chaque événement que vous souhaitez auditer.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-109">To change the audit options, select the check boxes for each event you want to audit.</span></span> <span data-ttu-id="4a2d5-110">Les événements disponibles sont l’enregistrement des paramètres modifiés, renvoyés réussie d’une erreur après avoir modifié et Échec lors de la soumettre à nouveau une erreur.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-110">The available events are the saving of modified settings, successful resubmission of a fault after editing, and failure when resubmitting a fault.</span></span>  
  
-   <span data-ttu-id="4a2d5-111">Le portail gère une file d’attente des alertes générées par le service d’alerte.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-111">The portal maintains a queue of the alerts generated by the Portal Alert service.</span></span> <span data-ttu-id="4a2d5-112">Vous pouvez modifier les paramètres pour ce service dans le **Options d’alerte pour file d’attente** section de la page.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-112">You can modify the settings for this service in the **Alert Queue Options** section of the page.</span></span> <span data-ttu-id="4a2d5-113">Vous pouvez activer ou désactiver le service, spécifiez son interaction avec le service d’annuaire Microsoft Active Directory et contrôler la taille de lot de file d’attente et l’intervalle d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-113">You can enable or disable the service, specify its interaction with Microsoft Active Directory directory service, and control the queue batch size and polling interval.</span></span>  
  
-   <span data-ttu-id="4a2d5-114">Pour modifier les paramètres pour le service d’alertes par courrier électronique, utilisez les contrôles dans le **Options d’alerte par courrier électronique** section de la page.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-114">To change the settings for the Alert Email service, use the controls in the **Alert Email Options** section of the page.</span></span> <span data-ttu-id="4a2d5-115">Vous pouvez activer ou désactiver le service ; Spécifiez le serveur de messagerie et l’adresse « de » ; modifier la taille d’interrogation intervalle et le traitement par lots ; et spécifiez le chemin d’accès aux fichiers XSLT utilisé par le service.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-115">You can enable or disable the service; specify the e-mail server and the "from" address; change the polling interval and batch size; and specify the path to XSLT files that the service uses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a2d5-116">Lorsque vous installez et configurez le portail ESB et le service d’alerte de portail, vous devez entrer les valeurs dans cette page.</span><span class="sxs-lookup"><span data-stu-id="4a2d5-116">You must enter the values in this page when you install and configure the ESB Portal and the Portal Alert service.</span></span> <span data-ttu-id="4a2d5-117">Pour plus d’informations, consultez [l’installation du portail de gestion ESB](http://go.microsoft.com/fwlink/?LinkId=188554).</span><span class="sxs-lookup"><span data-stu-id="4a2d5-117">For more information, see [Installing the ESB Management Portal](http://go.microsoft.com/fwlink/?LinkId=188554).</span></span>