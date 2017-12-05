---
title: "Schémas de message pour les procédures stockées, fonctions et API PL-SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d707f10-470d-4390-bb5b-0301c326f375
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029c48c1e6066d09d43da51b2bb1f6786a516f54
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="ebe8a-102">Schémas de message pour les procédures stockées, fonctions et API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="ebe8a-102">Message Schemas for Stored Procedures, Functions, and PL/SQL APIs</span></span>
<span data-ttu-id="ebe8a-103">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces Oracle sous-jacentes de base de données des procédures stockées, des fonctions et des API PL/SQL (procédures stockées et fonctions dans un package) en tant qu’opérations.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces the underlying Oracle database stored procedures, functions, and PL/SQL APIs (stored procedures and functions within a package) as operations.</span></span> <span data-ttu-id="ebe8a-104">Cette section décrit la structure des messages et les actions utilisées pour appeler des procédures stockées, fonctions et les API PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-104">This section describes the message structure and actions used to invoke stored procedures, functions, and PL/SQL APIs.</span></span>  
  
## <a name="message-structure-of-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="ebe8a-105">Structure des messages de procédures stockées, fonctions et API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="ebe8a-105">Message Structure of Stored Procedures, Functions, and PL/SQL APIs</span></span>  
 <span data-ttu-id="ebe8a-106">Les opérations signalées pour les fonctions et procédures stockées utilisent un modèle d’échange de message demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-106">The operations surfaced for functions and stored procedures follow a request-response message exchange pattern.</span></span> <span data-ttu-id="ebe8a-107">Le tableau suivant illustre la structure de ces messages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-107">The following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebe8a-108">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-108">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="ebe8a-109">Opération</span><span class="sxs-lookup"><span data-stu-id="ebe8a-109">Operation</span></span>|<span data-ttu-id="ebe8a-110">Message XML</span><span class="sxs-lookup"><span data-stu-id="ebe8a-110">XML Message</span></span>|<span data-ttu-id="ebe8a-111"> Description</span><span class="sxs-lookup"><span data-stu-id="ebe8a-111">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="ebe8a-112">Demande de procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-112">Stored Procedure Request</span></span>|`<[SP_NAME] xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="ebe8a-113">Prend en charge les paramètres Oracle et IN OUT dans le corps du message</span><span class="sxs-lookup"><span data-stu-id="ebe8a-113">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="ebe8a-114">Réponse de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-114">Stored Procedure Response</span></span>|`<[SP_NAME]Response xmlns="[VERSION]/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="ebe8a-115">Prend en charge Oracle OUT et dans les paramètres dans le corps du message</span><span class="sxs-lookup"><span data-stu-id="ebe8a-115">Supports Oracle OUT and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="ebe8a-116">Demande de la fonction</span><span class="sxs-lookup"><span data-stu-id="ebe8a-116">Function Request</span></span>|`<[FN_NAME] xmlns="[VERSION]/Functions/[SCHEMA] ">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[FN_NAME]>`|<span data-ttu-id="ebe8a-117">Prend en charge les paramètres Oracle et IN OUT dans le corps du message</span><span class="sxs-lookup"><span data-stu-id="ebe8a-117">Supports Oracle IN and IN OUT parameters in the message body</span></span>|  
|<span data-ttu-id="ebe8a-118">Réponse de la fonction</span><span class="sxs-lookup"><span data-stu-id="ebe8a-118">Function Response</span></span>|`<[FN_NAME]Response xmlns="[VERSION]/Functions/[SCHEMA]">   <[FN_NAME]Result>return_value</[FN_NAME]Result>   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   …    </[FN_NAME]Response>`|<span data-ttu-id="ebe8a-119">Prend en charge Oracle OUT et dans les paramètres dans le corps du message</span><span class="sxs-lookup"><span data-stu-id="ebe8a-119">Supports Oracle OUT and IN OUT parameters in the message body</span></span><br /><br /> <span data-ttu-id="ebe8a-120">La valeur de retour de fonction est retournée dans le \<[FN_NAME] résultat\> élément.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-120">The function return value is returned in the \<[FN_NAME]Result\> element.</span></span> <span data-ttu-id="ebe8a-121">Il s’agit du premier élément dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-121">This is the first element in the response message.</span></span> <span data-ttu-id="ebe8a-122">Il se situe avant tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-122">It comes before any parameters.</span></span>|  
|<span data-ttu-id="ebe8a-123">Demande d’API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="ebe8a-123">PL/SQL API Request</span></span>|`<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|<span data-ttu-id="ebe8a-124">Même en tant que fonction ou procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-124">Same as Function or Stored Procedure</span></span>|  
|<span data-ttu-id="ebe8a-125">Procédure empaquetée ou une réponse de la fonction</span><span class="sxs-lookup"><span data-stu-id="ebe8a-125">Packaged Procedure or Function Response</span></span>|`<[SP_NAME]Response xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]Response>`|<span data-ttu-id="ebe8a-126">Même en tant que fonction ou procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-126">Same as Function or Stored Procedure</span></span>|  
  
 <span data-ttu-id="ebe8a-127">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="ebe8a-127">Entity descriptions:</span></span>  
  
 <span data-ttu-id="ebe8a-128">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-128">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05.</span></span>  
  
 <span data-ttu-id="ebe8a-129">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-129">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="ebe8a-130">[SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-130">[SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.</span></span>  
  
 <span data-ttu-id="ebe8a-131">[FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-131">[FN_NAME] = The function to be executed; for example, FN_GETID.</span></span>  
  
 <span data-ttu-id="ebe8a-132">[PRM1_NAME] = le nom du paramètre Oracle.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-132">[PRM1_NAME] = The name of the Oracle parameter.</span></span> <span data-ttu-id="ebe8a-133">Consultez la colonne de Description pour les directions de paramètre pris en charge pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-133">See the Description column for supported parameter directions for each message.</span></span>  
  
 <span data-ttu-id="ebe8a-134">[PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-134">[PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.</span></span>  
  
 <span data-ttu-id="ebe8a-135">La base de données Oracle prend en charge la surcharge des fonctions et procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-135">The Oracle database supports overloading for stored procedures and functions.</span></span> <span data-ttu-id="ebe8a-136">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge cette fonctionnalité en ajoutant une chaîne de la surcharge de l’espace de noms cible pour chaque artefact surchargé.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-136">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports this capability by appending an overload string to the target namespace for each overloaded artifact.</span></span> <span data-ttu-id="ebe8a-137">La valeur de cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la seconde surcharge et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-137">The value of this string is "overload1" for the first overload, "overload2" for the second overload, and so on.</span></span> <span data-ttu-id="ebe8a-138">L’exemple suivant montre la structure du message pour les deux procédures stockées surchargés.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-138">The following example shows the message structure for two overloaded stored procedures.</span></span>  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="[VERSION]/PackageApis/[SCHEMA]/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
## <a name="message-actions-of-stored-procedures-functions-and-plsql-apis"></a><span data-ttu-id="ebe8a-139">Actions de message de procédures stockées, fonctions et API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="ebe8a-139">Message Actions of Stored Procedures, Functions, and PL/SQL APIs</span></span>  
 <span data-ttu-id="ebe8a-140">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les actions de message suivant de procédure stockée, fonction et les opérations d’API de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-140">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for stored procedure, function, and PL/SQL API operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebe8a-141">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-141">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="ebe8a-142">Message</span><span class="sxs-lookup"><span data-stu-id="ebe8a-142">Message</span></span>|<span data-ttu-id="ebe8a-143">Action</span><span class="sxs-lookup"><span data-stu-id="ebe8a-143">Action</span></span>|<span data-ttu-id="ebe8a-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebe8a-144">Example</span></span>|  
|-------------|------------|-------------|  
|<span data-ttu-id="ebe8a-145">Demande de procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-145">Stored Procedure Request</span></span>|<span data-ttu-id="ebe8a-146">Procédures / [schéma] / [SP_NAME]</span><span class="sxs-lookup"><span data-stu-id="ebe8a-146">Procedures/[SCHEMA]/[SP_NAME]</span></span>|<span data-ttu-id="ebe8a-147">Procédures/SCOTT/SP_INSERT</span><span class="sxs-lookup"><span data-stu-id="ebe8a-147">Procedures/SCOTT/SP_INSERT</span></span>|  
|<span data-ttu-id="ebe8a-148">Réponse de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-148">Stored Procedure Response</span></span>|<span data-ttu-id="ebe8a-149">Procédures / [schéma] / [SP_NAME] / réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-149">Procedures/[SCHEMA]/[SP_NAME]/response</span></span>|<span data-ttu-id="ebe8a-150">Procédures/SCOTT/SP_INSERT/réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-150">Procedures/SCOTT/SP_INSERT/response</span></span>|  
|<span data-ttu-id="ebe8a-151">Demande de la fonction</span><span class="sxs-lookup"><span data-stu-id="ebe8a-151">Function Request</span></span>|<span data-ttu-id="ebe8a-152">Fonctions / [schéma] / [FN_NAME]</span><span class="sxs-lookup"><span data-stu-id="ebe8a-152">Functions/[SCHEMA]/[FN_NAME]</span></span>|<span data-ttu-id="ebe8a-153">SCOTT/fonctions/FN_GETID</span><span class="sxs-lookup"><span data-stu-id="ebe8a-153">Functions/SCOTT/FN_GETID</span></span>|  
|<span data-ttu-id="ebe8a-154">Réponse de la fonction</span><span class="sxs-lookup"><span data-stu-id="ebe8a-154">Function Response</span></span>|<span data-ttu-id="ebe8a-155">Fonctions / [schéma] / [FN_NAME] / réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-155">Functions/[SCHEMA]/[FN_NAME]/response</span></span>|<span data-ttu-id="ebe8a-156">Fonctions/SCOTT/FN_GETID/réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-156">Functions/SCOTT/FN_GETID/response</span></span>|  
|<span data-ttu-id="ebe8a-157">Demande d’API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="ebe8a-157">PL/SQL API Request</span></span>|<span data-ttu-id="ebe8a-158">[Schéma] /Package/ [PACKAGE_NAME] / [SP_NAME]</span><span class="sxs-lookup"><span data-stu-id="ebe8a-158">[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]</span></span>|<span data-ttu-id="ebe8a-159">SCOTT/Package/CUSTOMER/SP_INSERT</span><span class="sxs-lookup"><span data-stu-id="ebe8a-159">SCOTT/Package/CUSTOMER/SP_INSERT</span></span>|  
|<span data-ttu-id="ebe8a-160">Empaqueté de réponse de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-160">Packaged Stored Procedure Response</span></span>|<span data-ttu-id="ebe8a-161">[Schéma] /Package/ [PACKAGE_NAME] / [SP_NAME] / réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-161">[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/response</span></span>|<span data-ttu-id="ebe8a-162">SCOTT/Package/CUSTOMER/SP_INSERT/réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-162">SCOTT/Package/CUSTOMER/SP_INSERT/response</span></span>|  
|<span data-ttu-id="ebe8a-163">Fonction packagée demande</span><span class="sxs-lookup"><span data-stu-id="ebe8a-163">Packaged Function Request</span></span>|<span data-ttu-id="ebe8a-164">[Schéma] /Package/ [PACKAGE_NAME] / [FN_NAME]</span><span class="sxs-lookup"><span data-stu-id="ebe8a-164">[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]</span></span>|<span data-ttu-id="ebe8a-165">SCOTT/Package/CUSTOMER/FN_GETID</span><span class="sxs-lookup"><span data-stu-id="ebe8a-165">SCOTT/Package/CUSTOMER/FN_GETID</span></span>|  
|<span data-ttu-id="ebe8a-166">Réponse de la fonction packagée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-166">Packaged Function Response</span></span>|<span data-ttu-id="ebe8a-167">[Schéma] /Package/ [PACKAGE_NAME] / [FN_NAME] / réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-167">[SCHEMA]/Package/[PACKAGE_NAME]/[FN_NAME]/response</span></span>|<span data-ttu-id="ebe8a-168">SCOTT/Package/CUSTOMER/FN_GETID/réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-168">SCOTT/Package/CUSTOMER/FN_GETID/response</span></span>|  
|<span data-ttu-id="ebe8a-169">Demande de la procédure stockée surchargée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-169">Overloaded Stored Procedure Request</span></span>|<span data-ttu-id="ebe8a-170">[Schéma] /Procedure/ [SP_NAME] / [surcharge]</span><span class="sxs-lookup"><span data-stu-id="ebe8a-170">[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]</span></span>|<span data-ttu-id="ebe8a-171">SCOTT/procédure/SP_INSERT/overload1</span><span class="sxs-lookup"><span data-stu-id="ebe8a-171">SCOTT/Procedure/SP_INSERT/overload1</span></span>|  
|<span data-ttu-id="ebe8a-172">Surchargée de réponse de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ebe8a-172">Overloaded Stored Procedure Response</span></span>|<span data-ttu-id="ebe8a-173">[Schéma] /Procedure/ [SP_NAME] / [surcharge] / réponse</span><span class="sxs-lookup"><span data-stu-id="ebe8a-173">[SCHEMA]/Procedure/[SP_NAME]/[OVERLOAD]/response</span></span>|<span data-ttu-id="ebe8a-174">SCOTT/procédure/SP_INSERT/overload1/réponse.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-174">SCOTT/Procedure/SP_INSERT/overload1/response</span></span>|  
  
 <span data-ttu-id="ebe8a-175">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="ebe8a-175">Entity descriptions:</span></span>  
  
 <span data-ttu-id="ebe8a-176">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-176">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="ebe8a-177">[SP_NAME] = la procédure stockée à exécuter ; par exemple, SP_INSERT.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-177">[SP_NAME] = The stored procedure to be executed; for example, SP_INSERT.</span></span>  
  
 <span data-ttu-id="ebe8a-178">[FN_NAME] = la fonction à exécuter ; par exemple, FN_GETID.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-178">[FN_NAME] = The function to be executed; for example, FN_GETID.</span></span>  
  
 <span data-ttu-id="ebe8a-179">[PACKAGE_NAME] = le nom du package qui contient la fonction ou procédure ciblé.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-179">[PACKAGE_NAME] = The name of the package that contains the targeted procedure or function.</span></span>  
  
 <span data-ttu-id="ebe8a-180">[Surcharge] = le paramètre de surcharger le.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-180">[OVERLOAD] = The Overload parameter.</span></span> <span data-ttu-id="ebe8a-181">Les valeurs possibles sont overload1, overload2 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ebe8a-181">The possible values are overload1, overload2, and so on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe8a-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebe8a-182">See Also</span></span>  
 [<span data-ttu-id="ebe8a-183">Messages et schémas de message pour l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="ebe8a-183">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)