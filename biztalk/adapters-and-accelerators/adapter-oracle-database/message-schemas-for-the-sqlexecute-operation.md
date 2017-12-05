---
title: "Schémas de message pour l’opération SQLEXECUTE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLEXECUTE operations, message schemas for
ms.assetid: 744645f4-0674-44e0-bf8d-8df70086b0f1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c7efc6a59e9dd4c163388803763a7b90a13b31
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-the-sqlexecute-operation"></a><span data-ttu-id="aa0cf-102">Schémas de message pour l’opération SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="aa0cf-102">Message Schemas for the SQLEXECUTE Operation</span></span>
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="aa0cf-103">met en évidence fortement typée de métadonnées pour les artefacts présents dans le système métier et expose des opérations standard sur ces artefacts.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-103"> surfaces strongly-typed metadata for artifacts present in the LOB system and exposes standard operations on these artifacts.</span></span> <span data-ttu-id="aa0cf-104">Toutefois, il existe des scénarios où une application peut nécessiter l’exécution d’une instruction SQL arbitraire piloté par la logique métier de l’application.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-104">However, there are scenarios where an application might require the execution of an arbitrary SQL statement that is driven by the business logic in the application.</span></span> <span data-ttu-id="aa0cf-105">Par exemple, vous souhaiterez :</span><span class="sxs-lookup"><span data-stu-id="aa0cf-105">For example, you may want to:</span></span>  
  
-   <span data-ttu-id="aa0cf-106">Effectuer une opération sur les artefacts de base de données qui ne sont pas signalées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; par exemple, obtenir le CURVAL ou NEXTVAL d’une séquence Oracle.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-106">Perform an operation on database artifacts that are not surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example, get the CURVAL or NEXTVAL of an Oracle SEQUENCE.</span></span>  
  
-   <span data-ttu-id="aa0cf-107">Effectuer des opérations de langage de définition de données ; par exemple, créer une table.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-107">Perform Data Definition Language operations; for example, create a table.</span></span>  
  
-   <span data-ttu-id="aa0cf-108">Effectuer des opérations sur un objet de base de données qui n’était pas présente au moment du design ; par exemple, mettre à jour des enregistrements dans une table temporaire qui est créé par votre logique métier.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-108">Perform operations on a database artifact that was not present at design-time; for example, update records in a temporary table that is created by your business logic.</span></span>  
  
-   <span data-ttu-id="aa0cf-109">Effectuer des opérations DML plus complexes sur les tables que les opérations exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; pour l’exemple montre comment exécuter une requête qui inclut une clause JOIN.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-109">Perform more complex DML operations on tables than the operations surfaced by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; for example perform a query that includes a JOIN clause.</span></span>  
  
 <span data-ttu-id="aa0cf-110">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence une opération spécial appelée l’opération SQLEXECUTE pour prendre en charge ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-110">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces a special operation called the SQLEXECUTE operation to support such scenarios.</span></span> <span data-ttu-id="aa0cf-111">À l’aide de cette opération, vous pouvez spécifier une instruction SQL arbitraire pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à exécuter sur la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-111">By using this operation, you can specify an arbitrary SQL statement for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to execute on the Oracle database.</span></span> <span data-ttu-id="aa0cf-112">Vous pouvez également spécifier plusieurs blocs de paramètres d’entrée de l’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-112">You can also specify multiple blocks of input parameters to the SQL statement.</span></span> <span data-ttu-id="aa0cf-113">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute l’instruction SQL qu’une seule fois pour chaque jeu de paramètres et retourne toute sortie sous la forme d’un jeu d’enregistrements (faiblement typée) générique.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes the SQL statement once for each set of parameters and returns any output as a generic (weakly-typed) record set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa0cf-114">Vous pouvez passer dans et dans les paramètres pour les procédures, fonctions et des packages dans l’opération SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-114">You can pass IN and IN OUT parameters to procedures, functions, and packages in the SQLEXECUTE operation.</span></span> <span data-ttu-id="aa0cf-115">L’artefact appelée s’exécute avec les paramètres fournis sur la base de données Oracle ; Toutefois, l’opération SQLEXECUTE ne retourne pas la valeur de sortie et dans les paramètres pour le client.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-115">The invoked artifact will execute with the supplied parameters on the Oracle database; however, the SQLEXECUTE operation does not return the value of OUT and IN OUT parameters to the client.</span></span> <span data-ttu-id="aa0cf-116">Si vous souhaitez appeler des procédures, fonctions ou des packages, Microsoft vous recommande de faire en appelant les opérations dédiées qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour que ces artefacts Oracle.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-116">If you want to invoke procedures, functions, or packages, Microsoft recommends that you do so by invoking the dedicated operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for these Oracle artifacts.</span></span>  
  
 <span data-ttu-id="aa0cf-117">Le code XML suivant montre la structure de l’opération SQLEXECUTE :</span><span class="sxs-lookup"><span data-stu-id="aa0cf-117">The following XML shows the structure of the SQLEXECUTE operation:</span></span>  
  
```  
<SQLEXECUTE xmlns="SQLEXECUTE">  
  <SQLSTATEMENT> [STATEMENT] </SQLSTATEMENT>  
  <PARAMETERSCHEMA>[PARAM_SPEC]</PARAMETERSCHEMA>  
  <PARAMETERSET>  
    <PARAMETERDATA>  
      <PARAMETER xmlns:c="http://schemas.microsoft.com/2003/10/Serialization/Arrays">  
        <c:string>[PARAM_VAL_1]</c:string>  
      </PARAMETER>  
    </PARAMETERDATA>  
    …  
  </PARAMETERSET>  
</SQLEXECUTE>  
```  
  
 <span data-ttu-id="aa0cf-118">[Instruction] = l’instruction SQL à exécuter ; par exemple, « sélectionnez * de la table emp WHERE matemp = : emp_no ».</span><span class="sxs-lookup"><span data-stu-id="aa0cf-118">[STATEMENT] = The SQL statement to execute; for example, "SELECT * from emp WHERE empno=:emp_no".</span></span>  
  
 <span data-ttu-id="aa0cf-119">[PARAM_SPEC] = la liste des paramètres IN dans l’instruction SQL et leurs types de données ; par exemple, « emp_no nombre ».</span><span class="sxs-lookup"><span data-stu-id="aa0cf-119">[PARAM_SPEC] = The list of the IN parameters in the SQL statement and their data types; for example, "emp_no NUMBER".</span></span>  
  
 <span data-ttu-id="aa0cf-120">[PARAM_VAL_1] = la valeur du premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-120">[PARAM_VAL_1] = The value of the first parameter.</span></span>  
  
 <span data-ttu-id="aa0cf-121">Chaque \<PARAMETERDATA\> section contient un ensemble complet de \<paramètre\> les éléments qui correspondent au schéma dans le \<PARAMETERSCHEMA\> section.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-121">Each \<PARAMETERDATA\> section contains a complete set of \<PARAMETER\> elements that match the schema in the \<PARAMETERSCHEMA\> section.</span></span> <span data-ttu-id="aa0cf-122">Le \<PARAMETERSET\> peut contenir plusieurs \<PARAMETERDATA\> sections.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-122">The \<PARAMETERSET\> can contain multiple \<PARAMETERDATA\> sections.</span></span> <span data-ttu-id="aa0cf-123">Si c’est le cas, l’instruction SQL est exécutée plusieurs fois, une fois par rapport à chaque jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa0cf-123">If this is the case, the SQL statement is executed multiple times, once against each parameter set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0cf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa0cf-124">See Also</span></span>  
 [<span data-ttu-id="aa0cf-125">Messages et schémas de message pour l’adaptateur BizTalk pour Oracle Database</span><span class="sxs-lookup"><span data-stu-id="aa0cf-125">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)