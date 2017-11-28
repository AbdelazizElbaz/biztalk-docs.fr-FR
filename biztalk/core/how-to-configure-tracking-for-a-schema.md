---
title: "Comment configurer le suivi pour un schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, configuring
- managing [schemas], configuring
- configuring [HAT tracking], schemas
- configuring, schemas
- configuring, tracking
- HAT, schemas
- managing [schemas], tracking
- schemas, tracking
- tracking, configuring
- tracking, schemas
ms.assetid: b5f69c98-8824-43b1-8f21-d84b60ac5431
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e15cb2210062901786b179ec75fe3880dea660b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-schema"></a><span data-ttu-id="b94cb-102">Configuration du suivi d'un schéma</span><span class="sxs-lookup"><span data-stu-id="b94cb-102">How to Configure Tracking for a Schema</span></span>
<span data-ttu-id="b94cb-103">Cette rubrique décrit la configuration du suivi d'un schéma à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b94cb-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure tracking for a schema.</span></span> <span data-ttu-id="b94cb-104">Pour configurer le suivi, vous spécifiez les propriétés de message que vous voulez afficher dans les vues de requête de la page Hub du groupe de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b94cb-104">To configure tracking, you specify the properties of the messages that you want to view in the query views of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console Group Hub page.</span></span>  
  
 <span data-ttu-id="b94cb-105">Pour plus d’informations sur la création et l’utilisation de requêtes, consultez [à l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="b94cb-105">For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span> <span data-ttu-id="b94cb-106">Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).</span><span class="sxs-lookup"><span data-stu-id="b94cb-106">For more information about the message event and service instance tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b94cb-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b94cb-107">Prerequisites</span></span>  
 <span data-ttu-id="b94cb-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b94cb-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b94cb-109">Si vous souhaitez n'afficher que les options de suivi, vous pouvez être connecté en tant que membre du groupe des opérateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b94cb-109">To you want to view tracking options only, you can be logged on as a member of the BizTalk Server Operators group.</span></span> <span data-ttu-id="b94cb-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b94cb-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-schema"></a><span data-ttu-id="b94cb-111">Pour configurer le suivi d'un schéma</span><span class="sxs-lookup"><span data-stu-id="b94cb-111">To configure tracking for a schema</span></span>  
  
1.  <span data-ttu-id="b94cb-112">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b94cb-112">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b94cb-113">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le schéma pour lequel vous voulez configurer le suivi, puis développez l’application contenant le schéma.</span><span class="sxs-lookup"><span data-stu-id="b94cb-113">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the schema for which you want to configure tracking, and then expand the application containing the schema.</span></span>  
  
3.  <span data-ttu-id="b94cb-114">Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b94cb-114">Click **Schemas**, right-click the schema, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b94cb-115">Dans le volet gauche, cliquez sur **suivi**.</span><span class="sxs-lookup"><span data-stu-id="b94cb-115">In the left pane, click **Tracking**.</span></span>  
  
5.  <span data-ttu-id="b94cb-116">Effectuez l’une des options suivantes pour spécifier les propriétés à utiliser pour le suivi des messages, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="b94cb-116">Do one of the following to specify which properties to use for tracking messages, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="b94cb-117">Sélectionnez le **sélectionner toutes les propriétés de message** case à cocher pour utiliser toutes les propriétés répertoriées.</span><span class="sxs-lookup"><span data-stu-id="b94cb-117">Select the **Select all message properties** check box to use all the listed properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b94cb-118">Cette case à cocher est disponible seulement pour les schémas qui contiennent des propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="b94cb-118">This check box is available only for schemas that contain promoted properties.</span></span>  
  
    -   <span data-ttu-id="b94cb-119">Activez la case à cocher de chaque propriété que vous voulez utiliser.</span><span class="sxs-lookup"><span data-stu-id="b94cb-119">Select the check box of each property that you want to use.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b94cb-120">Cette option est disponible seulement pour les schémas qui contiennent des propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="b94cb-120">This is available only for schemas that contain promoted properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b94cb-121">Il est conseillé de ne sélectionner que les options dont vous avez besoin, car le suivi des messages engendre une surcharge pour votre système, en matière de performances et de stockage.</span><span class="sxs-lookup"><span data-stu-id="b94cb-121">You should select only the options you need, as tracking messages creates performance and storage overhead for your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94cb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b94cb-122">See Also</span></span>  
 [<span data-ttu-id="b94cb-123">Gestion des schémas</span><span class="sxs-lookup"><span data-stu-id="b94cb-123">Managing Schemas</span></span>](../core/managing-schemas.md)