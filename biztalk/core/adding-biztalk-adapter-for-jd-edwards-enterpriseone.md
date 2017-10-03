---
title: "Ajout de l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, JD Edwards EnterpriseOne adapters
- JD Edwards EnterpriseOne adapters, installing
- adapters [JD Edwards EnterpriseOne adapters], installing
ms.assetid: baecebcd-c324-40aa-bacf-876f45b6c37f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ab141d8f3227c12abd9a790bc82fa8f9ada3ae8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="a54ee-102">Ajout de l'adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="a54ee-102">Adding BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="a54ee-103">L'adaptateur Microsoft BizTalk pour J.D.Edwards EnterpriseOne contient les dossiers des gestionnaires de réception et d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a54ee-103">Microsoft BizTalk Adapter for J.D.Edwards EnterpriseOne contains both the Receive Handler and Send Handler folders.</span></span> <span data-ttu-id="a54ee-104">Les dossiers incluent BizTalkServerApplication.</span><span class="sxs-lookup"><span data-stu-id="a54ee-104">The folders contain BizTalkServerApplication.</span></span> <span data-ttu-id="a54ee-105">L'adaptateur BizTalk pour J.D.Edwards EnterpriseOne peut être créé. Il est exécuté de façon In-process avec BizTalk Server et n'est pas exécuté dans un processus d'hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="a54ee-105">BizTalk Adapter for J.D.Edwards EnterpriseOne is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.</span></span>  
  
### <a name="to-add-the-adapter-to-biztalk-server"></a><span data-ttu-id="a54ee-106">Pour ajouter l'adaptateur à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a54ee-106">To add the adapter to BizTalk Server</span></span>  
  
1.  <span data-ttu-id="a54ee-107">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a54ee-107">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a54ee-108">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **paramètres de plateforme**.</span><span class="sxs-lookup"><span data-stu-id="a54ee-108">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="a54ee-109">Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="a54ee-109">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="a54ee-110">Tapez un nom pour l’adaptateur ; par exemple, `JDEEnterpriseOne`.</span><span class="sxs-lookup"><span data-stu-id="a54ee-110">Type a name for the adapter; for example, `JDEEnterpriseOne`.</span></span>  
  
5.  <span data-ttu-id="a54ee-111">Sélectionnez **JDEEnterpriseOne** à partir de la **carte** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a54ee-111">Select **JDEEnterpriseOne** from the **Adapter** list, and click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54ee-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a54ee-112">See Also</span></span>  
 [<span data-ttu-id="a54ee-113">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="a54ee-113">Developing Applications</span></span>](../core/developing-applications2.md)