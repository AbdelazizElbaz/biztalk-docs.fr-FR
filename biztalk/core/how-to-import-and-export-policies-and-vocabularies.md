---
title: "Comment importer et exporter des stratégies et des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, exporting
- Rule Engine Deployment Wizard
- policies, importing
- vocabularies, exporting
- vocabularies, importing
ms.assetid: c427f686-5908-4f72-9e72-46a5497274ac
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17ba7cd8a9fc5d28d1b718e9a47ad6cf2f448ec7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-and-export-policies-and-vocabularies"></a><span data-ttu-id="beccd-102">Comment importer et exporter des stratégies et des vocabulaires</span><span class="sxs-lookup"><span data-stu-id="beccd-102">How to Import and Export Policies and Vocabularies</span></span>
<span data-ttu-id="beccd-103">L'Assistant Déploiement du moteur de règles permet d'importer ou d'exporter une stratégie ou un vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="beccd-103">You can use the Rules Engine Deployment Wizard to import or export a policy or vocabulary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beccd-104">Tous les vocabulaires utilisés par une stratégie ou un vocabulaire doivent d'abord être importés, sinon une erreur sera générée.</span><span class="sxs-lookup"><span data-stu-id="beccd-104">All vocabularies used by a policy or vocabulary must be imported first or you will get an error.</span></span>  
  
### <a name="to-import-or-export-a-policy-or-vocabulary"></a><span data-ttu-id="beccd-105">Pour importer ou exporter une stratégie ou un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="beccd-105">To import or export a policy or vocabulary</span></span>  
  
1.  <span data-ttu-id="beccd-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="beccd-106">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="beccd-107">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="beccd-107">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="beccd-108">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="beccd-108">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="beccd-109">Dans la page d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-109">On the welcome page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="beccd-110">Sur le **la tâche de déploiement** page, sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données** ou **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis Cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-110">On the **Deployment Task** page, select either **Export Policy/Vocabulary to file from database** or **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="beccd-111">Sur le **magasin de stratégies** page, dans la liste déroulante, sélectionnez un ordinateur SQL Server disponible et base de données, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-111">On the **Policy Store** page, from the drop-down lists, select an available SQL Server computer and database, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="beccd-112">Sur le **Exporter stratégie/vocabulaire** page, procédez comme suit, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-112">On the **Export Policy/Vocabulary** page, do the following, and then click **Next**.</span></span>  
  
    1.  <span data-ttu-id="beccd-113">Sélectionnez **stratégie** ou **vocabulaire** selon ce que vous voulez d’exportation/importation.</span><span class="sxs-lookup"><span data-stu-id="beccd-113">Select **Policy** or **Vocabulary** depending on what you want to export/import.</span></span>  
  
    2.  <span data-ttu-id="beccd-114">À partir de la **stratégie/le vocabulaire** liste déroulante, sélectionnez la stratégie/le vocabulaire souhaité.</span><span class="sxs-lookup"><span data-stu-id="beccd-114">From the **Policy/Vocabulary** drop-down list, select the desired policy/vocabulary.</span></span>  
  
    3.  <span data-ttu-id="beccd-115">Cliquez sur **Parcourir** pour sélectionner le fichier de définition.</span><span class="sxs-lookup"><span data-stu-id="beccd-115">Click **Browse** to select the definition file.</span></span>  
  
6.  <span data-ttu-id="beccd-116">Passez en revue le serveur, base de données et les informations de stratégie ou de vocabulaire, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-116">Review the server, database, and policy or vocabulary information, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="beccd-117">Une fois l’importation ou l’exportation terminée, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="beccd-117">After the import or export is completed, click **Next**.</span></span>  
  
8.  <span data-ttu-id="beccd-118">Passez en revue l’état d’achèvement de l’importation ou l’exportation, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="beccd-118">Review the completion status of the import or export, and then click **Finish**.</span></span>