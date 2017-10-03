---
title: "Étapes du scénario Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77751c15-9b67-4587-8bc8-2be65f13d339
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff3b2feda86ad0b8edbbded26a290c7276a63af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-solution-steps"></a><span data-ttu-id="44483-102">Étapes Solution du scénario</span><span class="sxs-lookup"><span data-stu-id="44483-102">Scenario Solution Steps</span></span>
<span data-ttu-id="44483-103">L’infrastructure de gestion d’Exception ESB fournit une solution simple pour gérer une exception lorsqu’un message de facture contient des données non valides qui provoque une erreur lors du traitement, comme décrit précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="44483-103">The ESB Exception Management Framework provides a simple solution for handling an exception when an invoice message contains invalid data that causes an error during processing, as described earlier in this topic.</span></span> <span data-ttu-id="44483-104">Voici une approche, que vous pouvez prendre :</span><span class="sxs-lookup"><span data-stu-id="44483-104">The following is one approach you could take:</span></span>  
  
1.  <span data-ttu-id="44483-105">Affecter la responsabilité de l’application récemment déployée Financial Reporting, basée sur Microsoft BizTalk à un développeur de votre équipe.</span><span class="sxs-lookup"><span data-stu-id="44483-105">Assign responsibility for the recently deployed Financial Reporting application based on Microsoft BizTalk to a developer on your team.</span></span>  
  
2.  <span data-ttu-id="44483-106">Un nouveau message d’erreur ESB arrive dans le portail de gestion ESB ; le message indique un problème d’intégrité de données dans une orchestration dans l’application BizTalk de création de rapports financiers.</span><span class="sxs-lookup"><span data-stu-id="44483-106">A new ESB fault message arrives in the ESB Management Portal; the message indicates a data integrity issue in an orchestration in the Financial Reporting BizTalk application.</span></span>  
  
3.  <span data-ttu-id="44483-107">L’administrateur ou opérateur notifie le développeur de la nouvelle exception, ou le développeur inscrit pour la notification automatique lorsqu’une exception se produit.</span><span class="sxs-lookup"><span data-stu-id="44483-107">The administrator or operator notifies the developer of the new exception, or the developer registers for automatic notification when an exception occurs.</span></span> <span data-ttu-id="44483-108">Cette notification peut se produire pour l’une des raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="44483-108">This notification may occur for one of the following reasons:</span></span>  
  
    -   <span data-ttu-id="44483-109">Il peut se produire, car l’exception dépassé un seuil prédéfini dans basés sur les événements d’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="44483-109">It may occur because the exception exceeded a threshold predefined in event-based Business Activity Monitoring (BAM).</span></span>  
  
    -   <span data-ttu-id="44483-110">Il peut se produire, car il existe un abonnement de BizTalk pour l’application spécifique, service, étendue et code d’erreur qui transfère l’exception au développeur.</span><span class="sxs-lookup"><span data-stu-id="44483-110">It may occur because a BizTalk subscription exists for the specific application, service, scope, and fault code that forwards the exception to the developer.</span></span>  
  
4.  <span data-ttu-id="44483-111">Le développeur examine le message d’erreur, les messages individuels d’orchestration et leurs valeurs de propriété de contexte persistante.</span><span class="sxs-lookup"><span data-stu-id="44483-111">The developer examines the fault message, the individual orchestration messages, and their persisted context property values.</span></span> <span data-ttu-id="44483-112">Les développeurs peuvent afficher ces informations via le portail de gestion ESB ou à l’aide de Microsoft Outlook via un abonnement de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="44483-112">Developers can view this information through the ESB Management Portal or by using Microsoft Outlook through a BizTalk subscription.</span></span>  
  
5.  <span data-ttu-id="44483-113">Le développeur détermine qu’il s’agit d’une erreur courante.</span><span class="sxs-lookup"><span data-stu-id="44483-113">The developer determines that this is a common error.</span></span> <span data-ttu-id="44483-114">Cela nécessite une intervention manuelle et la correction par l’équipe Finances, suivie de la nouvelle soumission dans le système.</span><span class="sxs-lookup"><span data-stu-id="44483-114">It will require manual intervention and correction by the Finance team, followed by resubmission to the system.</span></span>  
  
6.  <span data-ttu-id="44483-115">Le développeur crée et déploie un projet d’orchestration BizTalk indépendant qui s’abonne pour le type d’application et de l’exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="44483-115">The developer creates and deploys an independent BizTalk orchestration project that subscribes to the specific application and exception type.</span></span>  
  
7.  <span data-ttu-id="44483-116">Le projet d’orchestration récupère le message non valide à partir du message d’erreur ESB envoie le message à l’équipe Finances pour la correction, met en corrélation le message corrigé à l’orchestration et le renvoie s’il.</span><span class="sxs-lookup"><span data-stu-id="44483-116">The orchestration project retrieves the invalid message from the ESB fault message, sends the message to the Finance team for correction, correlates the corrected message back to the orchestration, and resubmits it.</span></span>  
  
8.  <span data-ttu-id="44483-117">Une semaine plus tard, le développeur accède au portail de gestion ESB pour découvrir que les tendances exception d’application pour les messages non valides ont considérablement diminué, car cette solution a été déployée.</span><span class="sxs-lookup"><span data-stu-id="44483-117">A week later, the developer navigates to the ESB Management Portal to discover that application exception trends for invalid messages have decreased dramatically since this solution was deployed.</span></span>