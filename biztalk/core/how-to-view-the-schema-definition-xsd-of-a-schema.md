---
title: "Comment afficher la définition de schéma (XSD) d’un schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, viewing
- managing [schemas], viewing
- viewing, schema definitions
- schemas, schema definition (XSD)
- managing [schemas], schema definition (XSD)
ms.assetid: 21b6d9e6-5737-4334-9fe6-15ae01f90c0d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 941951398ec966dea0045283e13c4581f60016aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-the-schema-definition-xsd-of-a-schema"></a><span data-ttu-id="d1a93-102">Affichage du langage XSD (XML Schema Definition) d'un schéma</span><span class="sxs-lookup"><span data-stu-id="d1a93-102">How to View the Schema Definition (XSD) of a Schema</span></span>
<span data-ttu-id="d1a93-103">Cette rubrique décrit comment afficher le langage XSD d'un schéma à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d1a93-103">This topic describes how to use the BizTalk Server Administration console to view the schema definition (XSD) of a schema.</span></span> <span data-ttu-id="d1a93-104">Cela vous permet de dépanner les erreurs de validation du schéma ou de valider le déploiement du schéma correct.</span><span class="sxs-lookup"><span data-stu-id="d1a93-104">You might want to do this to troubleshoot schema validation errors or validate that the correct schema is deployed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d1a93-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d1a93-105">Prerequisites</span></span>  
 <span data-ttu-id="d1a93-106">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server ou Opérateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d1a93-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> <span data-ttu-id="d1a93-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="d1a93-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-xsd-of-a-schema"></a><span data-ttu-id="d1a93-108">Pour afficher le langage XSD d'un schéma</span><span class="sxs-lookup"><span data-stu-id="d1a93-108">To view the XSD of a schema</span></span>  
  
1.  <span data-ttu-id="d1a93-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="d1a93-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d1a93-110">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le schéma pour lequel vous souhaitez afficher le langage XSD, puis développez l’application contenant le schéma.</span><span class="sxs-lookup"><span data-stu-id="d1a93-110">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to view the XSD, and then expand the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="d1a93-111">Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d1a93-111">Click **Schemas**, right-click the schema, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="d1a93-112">Dans le volet gauche, cliquez sur **vue schéma**.</span><span class="sxs-lookup"><span data-stu-id="d1a93-112">In the left pane, click **Schema View**.</span></span>  
  
     <span data-ttu-id="d1a93-113">Le langage XSD s'affiche dans le volet de droite.</span><span class="sxs-lookup"><span data-stu-id="d1a93-113">The XSD displays in the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a93-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1a93-114">See Also</span></span>  
 [<span data-ttu-id="d1a93-115">Gestion des schémas</span><span class="sxs-lookup"><span data-stu-id="d1a93-115">Managing Schemas</span></span>](../core/managing-schemas.md)