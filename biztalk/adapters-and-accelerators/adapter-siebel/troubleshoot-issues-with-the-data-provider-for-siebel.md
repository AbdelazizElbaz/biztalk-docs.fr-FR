---
title: "Résoudre les problèmes avec le fournisseur de données pour Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, troubleshooting
- troubleshooting, Data Provider for Siebel
ms.assetid: 2bfe69a2-d6de-466d-9f36-f11c386c771c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6e100635b1cb2db5c78ff713c8e6ad32d4e7d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-siebel"></a><span data-ttu-id="02421-102">Résoudre les problèmes avec le fournisseur de données pour Siebel</span><span class="sxs-lookup"><span data-stu-id="02421-102">Troubleshoot Issues with the Data Provider for Siebel</span></span>
<span data-ttu-id="02421-103">Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs que vous pouvez rencontrer lorsque vous utilisez la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="02421-103">This section discusses using troubleshooting techniques to resolve errors that you might encounter when using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="02421-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="02421-104">Known Issues</span></span>  
  
### <a name="data-provider-for-siebel-may-give-component-datareader-source-380-error"></a><span data-ttu-id="02421-105">Fournisseur de données pour Siebel peut provoquer l’erreur de « composant « DataReader Source' (380) »</span><span class="sxs-lookup"><span data-stu-id="02421-105">Data Provider for Siebel may give "component 'DataReader Source' (380)" error</span></span>  
 <span data-ttu-id="02421-106">**Problème**</span><span class="sxs-lookup"><span data-stu-id="02421-106">**Problem**</span></span>  
  
 <span data-ttu-id="02421-107">Lors de l’exécution d’une requête SELECT sur un composant d’entreprise Siebel, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] peut provoquer une erreur « composant « DataReader Source' (380) ».</span><span class="sxs-lookup"><span data-stu-id="02421-107">While performing a SELECT query on a Siebel business component, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] may give a "component 'DataReader Source' (380)" error.</span></span>  
  
 <span data-ttu-id="02421-108">**Cause**</span><span class="sxs-lookup"><span data-stu-id="02421-108">**Cause**</span></span>  
  
 <span data-ttu-id="02421-109">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] génère cette erreur si la valeur reçue à partir du système Siebel pour un paramètre dépasse la propriété maxLength pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="02421-109">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] gives this error if the value received from the Siebel system for a parameter exceeds the maxLength property for the parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02421-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02421-110">See Also</span></span>  
[<span data-ttu-id="02421-111">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="02421-111">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)