---
title: "Schémas de message pour REF CURSOR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REF CURSORS, message schemas for
- IN REF CURSOR
- OUT REF CURSOR
- IN OUT REF CURSOR
ms.assetid: b62e7a9f-278c-41b3-90f0-2f621a34327b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bddfde0b0897c7d8c21a20126d2fa1d2f0f8c78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-ref-cursors"></a><span data-ttu-id="2731d-102">Schémas de message pour REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="2731d-102">Message Schemas for REF CURSORS</span></span>
<span data-ttu-id="2731d-103">Un REF CURSOR est un type de données Oracle PL/SQL qui représente un pointeur vers un jeu de résultats dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="2731d-103">A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="2731d-104">Types de REF CURSOR activer l’entrée et de sortie de diffusion en continu de données et sont idéaux pour le transfert de grandes quantités de données vers et depuis un bloc de code PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="2731d-104">REF CURSOR types enable input and output streaming of data and are ideal for transferring large amounts of data to and from a PL/SQL code block.</span></span> [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]<span data-ttu-id="2731d-105">prend en charge en passant les paramètres REF CURSOR fortement typée et faiblement typée procédures PL/SQL et les fonctions, OUT et dans les paramètres.</span><span class="sxs-lookup"><span data-stu-id="2731d-105"> provides support for passing strongly-typed and weakly-typed REF CURSOR parameters to PL/SQL procedures and functions as IN, OUT and IN OUT parameters.</span></span>  
  
 <span data-ttu-id="2731d-106">Dans la base de données Oracle, un type de REF CURSOR peut être soit fortement typée ou faiblement typé :</span><span class="sxs-lookup"><span data-stu-id="2731d-106">In the Oracle database, a REF CURSOR type can be either strongly-typed or weakly-typed:</span></span>  
  
-   <span data-ttu-id="2731d-107">REF CURSOR fortement typée est déclaré avec une clause RETURN comme dans `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`.</span><span class="sxs-lookup"><span data-stu-id="2731d-107">A strongly-typed REF CURSOR is declared with a RETURN clause as in `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`.</span></span> <span data-ttu-id="2731d-108">Une variable de REF CURSOR fortement typé peut représenter uniquement un jeu de résultats qui contient des données qui correspond au type avec lequel son type REF CURSOR est déclaré.</span><span class="sxs-lookup"><span data-stu-id="2731d-108">A strongly-typed REF CURSOR variable can only represent a result set that contains data that matches the type with which its REF CURSOR type is declared.</span></span> <span data-ttu-id="2731d-109">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] renvoie un résultat fortement typée pour REF CURSOR fortement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-109">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a strongly-typed result set for a strongly-typed REF CURSOR.</span></span>  
  
-   <span data-ttu-id="2731d-110">REF CURSOR faiblement typée est déclaré sans clause de retour comme dans `TYPE WeakCurType IS REF CURSOR;`.</span><span class="sxs-lookup"><span data-stu-id="2731d-110">A weakly-typed REF CURSOR is declared without a RETURN clause as in `TYPE WeakCurType IS REF CURSOR;`.</span></span> <span data-ttu-id="2731d-111">Oracle fournit également un type spécial de REF CURSOR appelé SYS_REFCURSOR qui peut être utilisé pour déclarer des variables de REF CURSOR faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-111">Oracle also provides a special REF CURSOR type called SYS_REFCURSOR that can be used to declare weakly-typed REF CURSOR variables.</span></span> <span data-ttu-id="2731d-112">Variables de REF CURSOR faiblement typée peuvent représenter un jeu de résultats contenant n’importe quel type de données de ligne.</span><span class="sxs-lookup"><span data-stu-id="2731d-112">Weakly-typed REF CURSOR variables can represent a result set that contains any kind of row data.</span></span> <span data-ttu-id="2731d-113">La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] retourne un jeu de résultats de faiblement typé d’enregistrements génériques pour REF CURSOR faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a weakly-typed result set of generic records for a weakly-typed REF CURSOR.</span></span>  
  
## <a name="in-ref-cursor-parameters"></a><span data-ttu-id="2731d-114">DANS les paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="2731d-114">IN REF CURSOR Parameters</span></span>  
 <span data-ttu-id="2731d-115">Il n’existe aucune API ODP.NET pour créer un REF CURSOR sur le serveur Oracle, donc la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne peut pas fournir la capacité d’un programme client créer et gérer les variables de REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-115">There is no ODP.NET API to create a REF CURSOR on the Oracle server, so the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] cannot provide the capability for a client program to create and maintain REF CURSOR variables.</span></span>  
  
 <span data-ttu-id="2731d-116">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est le cas, toutefois, activer un client de passer des paramètres IN REF CURSOR à des fonctions ou des procédures stockées en spécifiant un bloc de code PL/SQL qui retourne les REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-116">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does, however, enable a client to pass IN REF CURSOR parameters to functions or stored procedures by specifying a block of PL/SQL code that returns a REF CURSOR.</span></span> <span data-ttu-id="2731d-117">L’adaptateur utilise ce code pour créer et ouvrir une variable REF CURSOR sur le serveur Oracle ; Ensuite, il appelle la fonction ou procédure stockée utilisant cette variable en tant que paramètre IN.</span><span class="sxs-lookup"><span data-stu-id="2731d-117">The adapter uses this code to create and OPEN a REF CURSOR variable on the Oracle server; it then calls the function or stored procedure using this variable as the IN parameter.</span></span>  
  
 <span data-ttu-id="2731d-118">La [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] représente des paramètres IN REF CURSOR en tant que chaînes contenant le bloc de code PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="2731d-118">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CURSOR parameters as strings that contain the PL/SQL code block.</span></span> <span data-ttu-id="2731d-119">Dans ce bloc, l’emplacement du curseur REF est spécifié avec un point d’interrogation ( ?).</span><span class="sxs-lookup"><span data-stu-id="2731d-119">Within this block, the location of the REF CURSOR is specified with a question mark (?).</span></span> <span data-ttu-id="2731d-120">Le bloc de code PL/SQL peut contenir une instruction OPEN-FOR qui contient une requête SQL ; ou elle peut contenir un appel de fonction ou une procédure dans laquelle un REF CURSOR ouverte est retourné dans un paramètre OUT.</span><span class="sxs-lookup"><span data-stu-id="2731d-120">The PL/SQL code block can contain an OPEN-FOR statement that contains a SQL query; or it can contain a function or procedure call in which an opened REF CURSOR is returned in an OUT parameter.</span></span>  
  
 <span data-ttu-id="2731d-121">Voici comment spécifier un en REF CURSOR en appelant une procédure stockée ou une fonction pour ouvrir le REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-121">The following shows how to specify an IN REF CURSOR by calling a stored procedure or function to open the REF CURSOR.</span></span>  
  
```  
<[IN_REF_CURSOR_PARAM_NAME]>begin [SP_NAME]([SP_PARAMS...], ?, [SP_PARAMS...]); end;</[IN_REF_CURSOR_PARAM_NAME]>  
  
Example:  
<EMP_RC>begin GETEMP(1, ?); end; </EMP_RC>  
```  
  
 <span data-ttu-id="2731d-122">Voici comment spécifier un en REF CURSOR à l’aide d’une requête SELECT pour ouvrir le REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-122">The following shows how to specify an IN REF CURSOR by using a SELECT query to open the REF CURSOR.</span></span>  
  
```  
<IN_REF_CURSOR_PARAM_NAME>begin open ? for select [FIELD_NAMES] from [TABLE_NAME]; end;</IN_REF_CURSOR_PARAM_NAME>  
  
Example:  
<EMP_RC>begin open ? for select * from EMP; end;</EMP_RC>  
```  
  
## <a name="out-ref-cursor-parameters"></a><span data-ttu-id="2731d-123">LES paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="2731d-123">OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="2731d-124">LES REF CURSOR paramètres sont retournés sous la forme des jeux de résultats de fortement typée ou faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-124">OUT REF CURSOR parameters are returned as either strongly-typed or weakly-typed result sets.</span></span> <span data-ttu-id="2731d-125">Le type de jeu de résultats retourné dépend de si le paramètre REF CURSOR est déclaré comme un REF CURSOR fortement typée ou faiblement typée dans la définition de procédure ou fonction stockée sur le serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="2731d-125">The type of the result set returned depends on whether the REF CURSOR parameter is declared as a strongly-typed or weakly-typed REF CURSOR in the stored procedure or function definition on the Oracle server.</span></span> <span data-ttu-id="2731d-126">Un jeu de résultats de fortement typé est retourné pour les paramètres REF CURSOR fortement typée et un jeu de résultats de faiblement typée est retourné pour faiblement typée des paramètres REF CURSOR (par exemple, les paramètres déclarés avec un type SYS_REFCURSOR).</span><span class="sxs-lookup"><span data-stu-id="2731d-126">A strongly-typed result set is returned for strongly-typed REF CURSOR parameters and a weakly-typed result set is returned for weakly-typed REF CURSOR parameters (for example, parameters declared with a SYS_REFCURSOR type).</span></span>  
  
 <span data-ttu-id="2731d-127">Le code suivant illustre le code XML pour un paramètre de sortie REF CURSOR fortement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-127">The following shows the XML for a strongly-typed OUT REF CURSOR parameter.</span></span>  
  
```  
<[PARAM_NAME]>  
 <[PARAM_NAME]RECORD>  
  <[COL1_NAME]>value1</[COL1_NAME]>  
  <[COL2_NAME]>value2</[COL2_NAME]>  
  ...  
 </[PARAM_NAME]RECORD>  
</[PARAM_NAME]>  
  
[PARAM_NAME] = OUT REF CURSOR parameter name; for example, EMP_REFCURSOR  
[COL_NAME] = Name of a column in the REF CURSOR type; for example, Name.  
```  
  
 <span data-ttu-id="2731d-128">Le code suivant illustre le code XML pour un paramètre de sortie REF CURSOR faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-128">The following shows the XML for a weakly-typed OUT REF CURSOR parameter.</span></span>  
  
```  
<[PARAM_NAME]>  
 <GenRecordRow xmlns="oracledb">  
  <GenRecordColumn>  
   <ColumnName>COL_NAME</ColumnName>  
   <ColumnValue>COL_VALUE</ColumnValue>  
   <ColumnType>COL_TYPE</ColumnType>  
  </GenRecordColumn>  
  …  
 </GenRecordRow>  
 …  
</[PARAM_NAME]>  
  
[COL_NAME] = Name of column; for example, Name  
[COL_VALUE] = Column value; for example, Scott  
[COL_TYPE] = Column data type; for example, System.String  
```  
  
## <a name="in-out-ref-cursor-parameters"></a><span data-ttu-id="2731d-129">DANS les paramètres REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="2731d-129">IN OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="2731d-130">Étant donné que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] modélise les paramètres IN REF CURSOR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes, il ne peut pas prendre en charge un seul type d’un paramètre dans des REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-130">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] models IN REF CURSOR parameters as strings and OUT REF CURSOR parameters as complex types, it cannot support a single type for an IN OUT REF CURSOR parameter.</span></span> <span data-ttu-id="2731d-131">Pour cette raison, il traite des paramètres dans des REF CURSOR comme deux paramètres différents : un paramètre IN dans le message de demande et d’un paramètre OUT dans le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="2731d-131">For this reason, it treats IN OUT REF CURSOR parameters as two different parameters: an IN parameter in the request message and an OUT parameter in the response message.</span></span>  
  
 <span data-ttu-id="2731d-132">Pour éviter un conflit de nom dans la programmation du modèle de service, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ajoute la chaîne « _IN » pour le paramètre IN dans le message de demande pour un paramètre donné nommé [PARAM_NAME], deux paramètres sont ainsi créés :</span><span class="sxs-lookup"><span data-stu-id="2731d-132">To avoid a name conflict in service model programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] appends the string "_IN" to the IN parameter in the request message so that for a given parameter named [PARAM_NAME], two parameters are created:</span></span>  
  
-   <span data-ttu-id="2731d-133">[PARAM_NAME] _IN est un paramètre IN REF CURSOR dans la procédure stockée ou d’un message de demande de fonction.</span><span class="sxs-lookup"><span data-stu-id="2731d-133">[PARAM_NAME]_IN is an IN REF CURSOR parameter in the stored procedure or function request message.</span></span> <span data-ttu-id="2731d-134">Il contient une instruction de PL/SQL (une requête select ou un appel de fonction ou procédure stocké) qui retourne les REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="2731d-134">It contains a PL/SQL statement (either a select query or a stored procedure or function call) that returns a REF CURSOR.</span></span>  
  
-   <span data-ttu-id="2731d-135">[PARAM_NAME] est un paramètre de sortie REF CURSOR dans la procédure stockée ou d’un message de réponse de fonction.</span><span class="sxs-lookup"><span data-stu-id="2731d-135">[PARAM_NAME] is an OUT REF CURSOR parameter in the stored procedure or function response message.</span></span> <span data-ttu-id="2731d-136">Il contient des REF CURSOR en tant qu’un jeu de résultats fortement typée ou faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="2731d-136">It contains the OUT REF CURSOR as a strongly-typed or weakly-typed result set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2731d-137">L’adaptateur ne peut pas prendre en charge une procédure ou fonction qui contient un paramètre IN nommé [PARAM_NAME] _IN et un paramètre dans les REF CURSOR nommé [PARAM_NAME].</span><span class="sxs-lookup"><span data-stu-id="2731d-137">The adapter cannot support a procedure or function that contains an IN parameter named [PARAM_NAME]_IN and an IN OUT REF CURSOR parameter named [PARAM_NAME].</span></span> <span data-ttu-id="2731d-138">Il s’agit, car l’adaptateur attend un paramètre nommé _IN [PARAM_NAME] pour représenter l’entrée pour le paramètre REF CURSOR et vous ne pouvez pas spécifier les deux paramètres dans le message de demande.</span><span class="sxs-lookup"><span data-stu-id="2731d-138">This is because the adapter expects a parameter named [PARAM_NAME]_IN to represent the input to the REF CURSOR parameter, and you cannot specify both parameters in the request message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2731d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2731d-139">See Also</span></span>  
 [<span data-ttu-id="2731d-140">Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="2731d-140">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)