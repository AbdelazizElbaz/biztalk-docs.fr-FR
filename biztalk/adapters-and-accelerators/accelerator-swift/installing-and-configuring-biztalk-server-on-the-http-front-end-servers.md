---
title: Installation et configuration de BizTalk Server sur les serveurs frontaux HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Server
- BizTalk Server, installing on HTTP servers
ms.assetid: dc1b3675-483a-478f-b30d-62efb73ad13c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 045a44c05789015d73bc797da14568d2cc3732f8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-http-front-end-servers"></a><span data-ttu-id="781b1-102">Installation et configuration de BizTalk Server sur les serveurs frontaux HTTP</span><span class="sxs-lookup"><span data-stu-id="781b1-102">Installing and Configuring BizTalk Server on the HTTP Front-End Servers</span></span>
<span data-ttu-id="781b1-103">Cette section décrit comment installer et configurer BizTalk Server à utiliser en tant que le serveur frontal HTTP pour l’hébergement du site MRSR et le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaires de modèle.</span><span class="sxs-lookup"><span data-stu-id="781b1-103">This section describes how to install and configure BizTalk Server to be used as the HTTP front-end server for hosting the MRSR site and the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] template forms.</span></span>  
  
### <a name="to-install-and-configure-biztalk-server-on-the-biztalk-http-front-end-servers"></a><span data-ttu-id="781b1-104">Pour installer et configurer BizTalk Server sur les serveurs frontaux HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="781b1-104">To install and configure BizTalk Server on the BizTalk HTTP front-end servers</span></span>  
  
1.  <span data-ttu-id="781b1-105">Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant les fonctionnalités suivantes : **moteur des règles d’entreprise** et **adaptateur SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="781b1-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing the following features: **Business Rules Engine** and **SharePoint Adapter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="781b1-106">Autres fonctionnalités ne sont pas requises pour cette installation.</span><span class="sxs-lookup"><span data-stu-id="781b1-106">Other features are not required for this installation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="781b1-107">Sur l’un des serveurs frontaux HTTP BizTalk, lorsque vous effectuez la configuration, créez le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="781b1-107">On one of the BizTalk HTTP front-end servers, when you perform configuration, create the BizTalk Group.</span></span>  
  
2.  <span data-ttu-id="781b1-108">Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="781b1-108">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="781b1-109">Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.</span><span class="sxs-lookup"><span data-stu-id="781b1-109">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span>