---
title: "Déterminer si une colonne stocke des valeurs en minuscules ou majuscules | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1edc8332-d8c7-4040-895b-f121fb03df44
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b54c00b43192462fb095dbfbfda4cbf0b248a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="determining-whether-a-column-stores-lowercase-or-uppercase-values"></a><span data-ttu-id="3c319-102">Déterminer si une colonne stocke les valeurs en minuscules ou majuscules</span><span class="sxs-lookup"><span data-stu-id="3c319-102">Determining Whether a Column Stores Lowercase or Uppercase Values</span></span>
<span data-ttu-id="3c319-103">Cette section répertorie les tâches principales à effectuer sur le système SAP pour déterminer si une colonne dans une table SAP stocke des caractères en minuscules ou majuscules.</span><span class="sxs-lookup"><span data-stu-id="3c319-103">This section lists high-level tasks to be performed on the SAP system to determine whether a column in an SAP table stores lowercase or uppercase characters.</span></span> <span data-ttu-id="3c319-104">Pour obtenir des instructions détaillées sur la façon d’effectuer cette tâche, vous devez contacter votre administrateur SAP ou consultez la documentation de SAP.</span><span class="sxs-lookup"><span data-stu-id="3c319-104">For detailed instructions on how to perform this task you must contact your SAP administrator or refer to SAP documentation.</span></span>  
  
### <a name="to-determine-the-case-of-values-stored-in-a-column"></a><span data-ttu-id="3c319-105">Pour déterminer le cas des valeurs stockées dans une colonne</span><span class="sxs-lookup"><span data-stu-id="3c319-105">To determine the case of values stored in a column</span></span>  
  
1.  <span data-ttu-id="3c319-106">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="3c319-106">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="3c319-107">Transaction SE37 et exécutez DDIF_TABL_GET.</span><span class="sxs-lookup"><span data-stu-id="3c319-107">Go to Transaction SE37 and execute DDIF_TABL_GET.</span></span>  
  
3.  <span data-ttu-id="3c319-108">Pour le paramètre NAME, spécifiez le nom de la table contenant la colonne pour laquelle vous souhaitez déterminer les informations de cas de caractères.</span><span class="sxs-lookup"><span data-stu-id="3c319-108">For the NAME parameter, specify the table name containing the column for which you want to determine the character case information.</span></span> <span data-ttu-id="3c319-109">Par exemple, KNA1.</span><span class="sxs-lookup"><span data-stu-id="3c319-109">For example, KNA1.</span></span>  
  
4.  <span data-ttu-id="3c319-110">Le premier paramètre de la table est DD03P_TAB.</span><span class="sxs-lookup"><span data-stu-id="3c319-110">The first table parameter is DD03P_TAB.</span></span> <span data-ttu-id="3c319-111">Cliquez sur le paramètre pour voir les lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="3c319-111">Click the parameter to see the rows in the table.</span></span> <span data-ttu-id="3c319-112">Chaque ligne de cette table correspond à une colonne dans la table (par exemple, KNA1) que vous avez spécifié à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="3c319-112">Every row in this table corresponds to a column in the table (such as KNA1) you specified in step 3.</span></span>  
  
5.  <span data-ttu-id="3c319-113">Dans DD03P_TAB, recherchez la valeur de la colonne en minuscules pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="3c319-113">In DD03P_TAB, look for the value in the LOWERCASE column for each row.</span></span> <span data-ttu-id="3c319-114">Si la valeur de la colonne en minuscules est « X », la colonne correspondante dans la table (par exemple, KNA1), peut stocker des caractères minuscules et majuscules.</span><span class="sxs-lookup"><span data-stu-id="3c319-114">If the value in the LOWERCASE column is 'X', the corresponding column in the table (such as KNA1), can store both lowercase and uppercase characters.</span></span> <span data-ttu-id="3c319-115">Si la valeur de la colonne en minuscules est vide, la colonne correspondante ne peut stocker que les caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="3c319-115">If the value in the LOWERCASE column is empty, the corresponding column can only store uppercase characters.</span></span>  
  
     <span data-ttu-id="3c319-116">Par exemple, pour la ligne de nom les minuscules colonne est X. Par conséquent, la colonne NAME dans KNA1 peut stocker des caractères majuscules et minuscules.</span><span class="sxs-lookup"><span data-stu-id="3c319-116">For example, for the NAME row the LOWERCASE column is X. So, the NAME column in KNA1 can store both uppercase and lowercase characters.</span></span> <span data-ttu-id="3c319-117">Toutefois, pour la ligne LAND1 les minuscules colonne est vide.</span><span class="sxs-lookup"><span data-stu-id="3c319-117">However, for the LAND1 row the LOWERCASE column is empty.</span></span> <span data-ttu-id="3c319-118">Par conséquent, la colonne LAND1 KNA1 table ne peut stocker que les caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="3c319-118">So, the LAND1 column in KNA1 table can only store uppercase characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c319-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c319-119">See Also</span></span>  
 [<span data-ttu-id="3c319-120">Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique</span><span class="sxs-lookup"><span data-stu-id="3c319-120">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)