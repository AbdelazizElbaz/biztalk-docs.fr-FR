---
title: "Single Sign-On : Événement 10589 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe962bb-e9bb-4107-a5fb-21c180d54e21
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56bb848711a627ceaea70085d770db7b0c759e9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10589"></a><span data-ttu-id="208e7-102">Single Sign-On : Événement 10589</span><span class="sxs-lookup"><span data-stu-id="208e7-102">Single Sign-On: Event 10589</span></span>
## <a name="details"></a><span data-ttu-id="208e7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="208e7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="208e7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="208e7-104">Product Name</span></span>|<span data-ttu-id="208e7-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="208e7-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="208e7-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="208e7-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="208e7-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="208e7-107">Event ID</span></span>|<span data-ttu-id="208e7-108">10589</span><span class="sxs-lookup"><span data-stu-id="208e7-108">10589</span></span>|  
|<span data-ttu-id="208e7-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="208e7-109">Event Source</span></span>|<span data-ttu-id="208e7-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="208e7-110">ENTSSO</span></span>|  
|<span data-ttu-id="208e7-111">Composant</span><span class="sxs-lookup"><span data-stu-id="208e7-111">Component</span></span>|<span data-ttu-id="208e7-112">Néant</span><span class="sxs-lookup"><span data-stu-id="208e7-112">N/A</span></span>|  
|<span data-ttu-id="208e7-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="208e7-113">Symbolic Name</span></span>|<span data-ttu-id="208e7-114">SSO_ERROR_BACKUP_SECRET_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="208e7-114">SSO_ERROR_BACKUP_SECRET_REQUIRED</span></span>|  
|<span data-ttu-id="208e7-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="208e7-115">Message Text</span></span>|<span data-ttu-id="208e7-116">Le secret principal n'a pas été sauvegardé.</span><span class="sxs-lookup"><span data-stu-id="208e7-116">The master secret has not been backed up.</span></span> <span data-ttu-id="208e7-117">Si vous perdez le secret principal, toutes les informations stockées dans le système d'authentification unique seront définitivement perdues et il se peut que vos systèmes ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="208e7-117">If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly.</span></span> <span data-ttu-id="208e7-118">Utilisez les outils d'administration de l'authentification unique pour sauvegarder votre secret principal.</span><span class="sxs-lookup"><span data-stu-id="208e7-118">Please use the SSO administration tools to back up your master secret.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="208e7-119">Explication</span><span class="sxs-lookup"><span data-stu-id="208e7-119">Explanation</span></span>  
 <span data-ttu-id="208e7-120">Le secret principal n'a pas été sauvegardé.</span><span class="sxs-lookup"><span data-stu-id="208e7-120">The master secret has not been backed up.</span></span> <span data-ttu-id="208e7-121">Si vous perdez le secret principal, toutes les informations stockées dans le système d'authentification unique seront définitivement perdues et il se peut que vos systèmes ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="208e7-121">If you lose the master secret all the information stored in the SSO system will be lost permanently and your systems may fail to work correctly.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="208e7-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="208e7-122">User Action</span></span>  
 <span data-ttu-id="208e7-123">Pour plus d’informations sur la sauvegarde du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).</span><span class="sxs-lookup"><span data-stu-id="208e7-123">For information on backing up the master secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>