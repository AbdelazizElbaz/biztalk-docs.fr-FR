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
# <a name="sending-idocs-from-an-sap-system"></a><span data-ttu-id="db836-102">Envoyer des IDOC à partir d’un système SAP</span><span class="sxs-lookup"><span data-stu-id="db836-102">Sending IDOCs from an SAP System</span></span>
<span data-ttu-id="db836-103">Tâches principales à effectuer sur le système SAP pour envoyer un IDOC à partir du système SAP à une application externe.</span><span class="sxs-lookup"><span data-stu-id="db836-103">High-level tasks to complete on the SAP system to send an IDOC from the SAP system to an external application.</span></span> <span data-ttu-id="db836-104">Contactez votre administrateur SAP pour effectuer ces tâches, ou reportez-vous à l’aide de SAP.</span><span class="sxs-lookup"><span data-stu-id="db836-104">Contact your SAP administrator for performing these tasks or see the SAP guidance.</span></span>  
  
## <a name="send-an-idoc-from-sap"></a><span data-ttu-id="db836-105">Envoyer un IDOC de SAP</span><span class="sxs-lookup"><span data-stu-id="db836-105">Send an IDOC from SAP</span></span>  
  
1.  <span data-ttu-id="db836-106">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="db836-106">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="db836-107">Créer un système logique à l’aide de la transaction de BD54.</span><span class="sxs-lookup"><span data-stu-id="db836-107">Create a logical system using BD54 transaction.</span></span>  
  
3.  <span data-ttu-id="db836-108">Créer une destination RFC dans les connexions TCP/IP à l’aide de la transaction de SM59.</span><span class="sxs-lookup"><span data-stu-id="db836-108">Create an RFC destination in TCP/IP connections using SM59 transaction.</span></span>  
  
4.  <span data-ttu-id="db836-109">Créer un port à l’aide de la transaction de WE21 et l’attacher à la destination RFC créée dans la dernière étape.</span><span class="sxs-lookup"><span data-stu-id="db836-109">Create a port using WE21 transaction and attach it to the RFC destination created in the last step.</span></span>  
  
5.  <span data-ttu-id="db836-110">Créer un profil de partenaire à l’aide de la transaction de WE20 avec le type de message requis et IDOC, puis l’attacher au port créé dans la dernière étape.</span><span class="sxs-lookup"><span data-stu-id="db836-110">Create a partner profile using WE20 transaction with the required message type and IDOC type, and then attach it to the port created in the last step.</span></span>  
  
6.  <span data-ttu-id="db836-111">Mettre à jour un modèle distribué en vous connectant le type de message pour le port à l’aide de la transaction de vente.</span><span class="sxs-lookup"><span data-stu-id="db836-111">Maintain a distributed model by connecting the message type to the port using the SALE transaction.</span></span>  
  
7.  <span data-ttu-id="db836-112">Générer un IDOC dans SAP.</span><span class="sxs-lookup"><span data-stu-id="db836-112">Generate an IDOC within SAP.</span></span> <span data-ttu-id="db836-113">Par exemple, utiliser les transactions BD10 pour déclencher un IDOC MATMAS.</span><span class="sxs-lookup"><span data-stu-id="db836-113">For example, use BD10 transaction to trigger a MATMAS IDOC.</span></span> <span data-ttu-id="db836-114">Pour plus d’informations sur les autres transactions pour déclencher des IDOC spécifiques, contactez votre administrateur SAP.</span><span class="sxs-lookup"><span data-stu-id="db836-114">Contact your SAP administrator for information about other transactions to trigger specific IDOCs.</span></span>  

## <a name="view-transaction-ids-in-sap"></a><span data-ttu-id="db836-115">Affichage des ID de Transaction dans SAP</span><span class="sxs-lookup"><span data-stu-id="db836-115">View Transaction IDs in SAP</span></span>
<span data-ttu-id="db836-116">Lorsque le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] appelle un tRFC ou envoie un IDOC à un système SAP, les registres de système SAP une transaction ID (TID) en réponse.</span><span class="sxs-lookup"><span data-stu-id="db836-116">When the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] invokes a tRFC or sends an IDOC to an SAP system, the SAP system registers a transaction ID (TID) in response.</span></span> <span data-ttu-id="db836-117">Dans certains scénarios, vous devez connaître le TID est inscrit avec le système SAP en réponse à un appel à partir de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db836-117">In some scenarios, you might need to know the TID that is registered with the SAP system in response to a call from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="db836-118">Par exemple, vous souhaiterez identifier l’unité logique de travail (LUW) sur le système SAP pour résoudre un problème.</span><span class="sxs-lookup"><span data-stu-id="db836-118">For example, you might want to identify the logical unit of work (LUW) on the SAP system to troubleshoot an issue.</span></span>  
  
 <span data-ttu-id="db836-119">Pour afficher le TID dans un système SAP, vous devez utiliser des transactions SM58.</span><span class="sxs-lookup"><span data-stu-id="db836-119">To view the TIDs in an SAP system, you must use transaction SM58.</span></span> <span data-ttu-id="db836-120">Contactez votre administrateur SAP ou consultez le Guide de SAP pour plus d’informations sur cette transaction.</span><span class="sxs-lookup"><span data-stu-id="db836-120">Contact your SAP administrator or refer to the SAP guidance for more information about this transaction.</span></span> 

## <a name="view-details-about-idocs-sent-and-received-from-sap"></a><span data-ttu-id="db836-121">Afficher les détails des IDOC envoyés et reçus à partir de SAP</span><span class="sxs-lookup"><span data-stu-id="db836-121">View details about IDOCs sent and received from SAP</span></span>
<span data-ttu-id="db836-122">À l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous pouvez envoyer un IDOC à un système SAP ou un IDOC de réception à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="db836-122">Using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you can send an IDOC to an SAP system or receive an IDOC from an SAP system.</span></span> <span data-ttu-id="db836-123">Pour suivre l’état et afficher les données d’un IDOC envoyé ou reçu par un système SAP, vous pouvez utiliser la transaction WE02.</span><span class="sxs-lookup"><span data-stu-id="db836-123">To track the status and view the data of an IDOC sent or received by an SAP system, you can use transaction WE02.</span></span> <span data-ttu-id="db836-124">Contactez votre administrateur SAP, ou consultez les conseils de SAP pour plus d’informations sur cette transaction.</span><span class="sxs-lookup"><span data-stu-id="db836-124">Contact your SAP administrator, or refer to the SAP guidance for more information about this transaction.</span></span>  

  
## <a name="see-also"></a><span data-ttu-id="db836-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db836-125">See Also</span></span>  
 [<span data-ttu-id="db836-126">Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique</span><span class="sxs-lookup"><span data-stu-id="db836-126">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)