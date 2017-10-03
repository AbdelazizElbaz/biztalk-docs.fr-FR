---
title: "Déploiement de règles de Validation de la devise-pays-BEI-BIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e96d416-d5eb-4597-a691-c7dbee33c7d6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65f1786b37194db25f0e38db7491538857f3406b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-bicbeicountrycurrency-validation-rules"></a><span data-ttu-id="19116-102">Déploiement de règles de Validation de BIC/BEI/pays/devise</span><span class="sxs-lookup"><span data-stu-id="19116-102">Deploying BIC/BEI/Country/Currency Validation Rules</span></span>
<span data-ttu-id="19116-103">**Pour déployer des règles de Validation de BIC/BEI/pays/devise :**</span><span class="sxs-lookup"><span data-stu-id="19116-103">**To deploy the BIC/BEI/Country/Currency Validation rules:**</span></span>  
  
1.  <span data-ttu-id="19116-104">Le jeu suivant de stratégies, % %Program files%\Microsoft BizTalk Accelerator pour les stratégies de Messages\Base SWIFT\SDK\MX, qui sont générique et non spécifique aux messages, devoir être publiées et déployés séparément à l’aide de l’Assistant Déploiement moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="19116-104">The following set of policies, %program files%\Microsoft BizTalk Accelerator for SWIFT\SDK\MX Messages\Base Policies, which are generic and not message-specific, need to be published and deployed separately using the Business Rule Engine Deployment Wizard.</span></span>  
  
    -   <span data-ttu-id="19116-105">MX_BIC_Master_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-105">MX_BIC_Master_Policy.xml</span></span>  
  
    -   <span data-ttu-id="19116-106">MX_BIC_Validation_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-106">MX_BIC_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="19116-107">MX_BEI_Validation_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-107">MX_BEI_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="19116-108">MX_DBConnection_Master_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-108">MX_DBConnection_Master_Policy.xml</span></span>  
  
    -   <span data-ttu-id="19116-109">MX_BICPlusIBAN_Validation_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-109">MX_BICPlusIBAN_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="19116-110">MX_SEPA_Validation_Policy.Xml</span><span class="sxs-lookup"><span data-stu-id="19116-110">MX_SEPA_Validation_Policy.xml</span></span>  
  
2.  <span data-ttu-id="19116-111">Avant de déployer ces stratégies, MX_DBConnection_Master_Policy.xml et MX_BIC_Master_Policy.xml doivent avoir le nom du serveur de base de données et le nom de la base de données où les valeurs de devise/pays ont été stockées.</span><span class="sxs-lookup"><span data-stu-id="19116-111">Before deploying these policies, MX_DBConnection_Master_Policy.xml and MX_BIC_Master_Policy.xml should have the database server name and database name where the Country/Currency values have been stored.</span></span>  
  
3.  <span data-ttu-id="19116-112">Une fois les stratégies maîtres ont été modifiés, publication, toutes les stratégies à l’aide de l’Assistant Déploiement moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="19116-112">Once the master policies have been modified, publish all polices using the Business Rule Engine Deployment Wizard.</span></span> <span data-ttu-id="19116-113">Utilisez l’option suivante : importer le fichier de stratégie/le vocabulaire vers la base de données.</span><span class="sxs-lookup"><span data-stu-id="19116-113">Use the following option: Import the policy/vocabulary file to database.</span></span>  
  
4.  <span data-ttu-id="19116-114">Cliquez sur Programmes, cliquez sur le serveur BizTalk \<version >, sur l’éditeur des règles d’entreprise et déployez-le sur les six publiés des stratégies.</span><span class="sxs-lookup"><span data-stu-id="19116-114">Click Programs, click BizTalk Server \<version>, click Business Rule Composer, and then deploy the six published polices.</span></span>