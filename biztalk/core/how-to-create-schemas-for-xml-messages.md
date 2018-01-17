---
title: "Comment créer des schémas pour les Messages XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0270293-fe23-42bd-b090-e877d5e9ce0b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6396d4607e93298961e6691ded2ca8d4566d819c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-create-schemas-for-xml-messages"></a><span data-ttu-id="f71df-102">Création de schémas pour les messages XML</span><span class="sxs-lookup"><span data-stu-id="f71df-102">How to Create Schemas for XML Messages</span></span>
<span data-ttu-id="f71df-103">Il existe plusieurs manières de créer des schémas de message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f71df-103">There are several methods for creating BizTalk message schemas.</span></span> <span data-ttu-id="f71df-104">Cette rubrique contient des instructions détaillées concernant certaines d'entre elles.</span><span class="sxs-lookup"><span data-stu-id="f71df-104">This topic provides step-by-step instructions for some of those methods.</span></span>  
  
### <a name="to-create-a-new-schema"></a><span data-ttu-id="f71df-105">Pour créer un nouveau schéma</span><span class="sxs-lookup"><span data-stu-id="f71df-105">To create a new schema</span></span>  
  
1.  <span data-ttu-id="f71df-106">Dans **l’Explorateur de solutions**, sélectionnez le projet BizTalk auquel vous souhaitez ajouter un schéma.</span><span class="sxs-lookup"><span data-stu-id="f71df-106">In **Solution Explorer**, select the BizTalk project to which you want to add a schema.</span></span>  
  
2.  <span data-ttu-id="f71df-107">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="f71df-107">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="f71df-108">Dans le **ajouter un nouvel élément - \< *BizTalk ProjectName* \>**  boîte de dialogue le **modèles** , cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="f71df-108">In the **Add New Item - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Schema**.</span></span>  
  
4.  <span data-ttu-id="f71df-109">Dans le **nom** zone, tapez un nom pour le schéma, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f71df-109">In the **Name** box, type a name for the schema, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="f71df-110">Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f71df-110">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
6.  <span data-ttu-id="f71df-111">Dans l’arborescence du schéma, sélectionnez le **schéma** nœud, puis, dans la fenêtre Propriétés, sélectionnez le **cible Namespace** propriété et tapez un nom pour l’espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="f71df-111">In the schema tree view, select the **Schema** node, and then in the Properties window, select the **Target Namespace** property and type a name for the target namespace.</span></span> <span data-ttu-id="f71df-112">Il est important que vous définissez cette propriété dans cette phase initiale de création de schéma ; Évitez d’utiliser la valeur par défaut **cible Namespace** valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="f71df-112">It is important that you set this property in this initial phase of schema creation; avoid using the default **Target Namespace** property value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f71df-113">Certains choix de noms effectués pour des fichiers de membre de projet tels que les fichiers de schéma peuvent provoquer des erreurs de compilation ultérieures en raison de conflits avec des mots réservés C# et des noms de type et d'espace de noms .NET Framework (« Système » par exemple).</span><span class="sxs-lookup"><span data-stu-id="f71df-113">Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as System).</span></span> <span data-ttu-id="f71df-114">schema.xsd, XmlContent et RootNodes sont des exemples de schémas.</span><span class="sxs-lookup"><span data-stu-id="f71df-114">Examples for schemas include schema.xsd, XmlContent, and RootNodes.</span></span> <span data-ttu-id="f71df-115">C’est parce que le **nom de Type** propriété valeur par défaut est la partie de base (sans extension) de la **nom de fichier** propriété.</span><span class="sxs-lookup"><span data-stu-id="f71df-115">This is because the **Type Name** property defaults to the base (non-extension) portion of the  **Filename** property.</span></span> <span data-ttu-id="f71df-116">Vous pouvez contourner ce type d’erreur de compilation en donnant explicitement la valeur de la **nom de Type** propriété à un élément qui n’est pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="f71df-116">You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f71df-117">Vous devrez peut-être ajouter, supprimer et modifier les enregistrements et les champs de votre schéma ainsi que les propriétés qui leur sont associées.</span><span class="sxs-lookup"><span data-stu-id="f71df-117">You may need to add, delete, and modify the records and fields in your schema along with their associated properties.</span></span> <span data-ttu-id="f71df-118">Pour plus d’informations, consultez [la gestion des nœuds dans un schéma](../core/managing-the-nodes-within-a-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f71df-118">To learn more about this, see [Managing the Nodes Within a Schema](../core/managing-the-nodes-within-a-schema.md).</span></span>  
  
### <a name="to-generate-a-schema-from-a-non-xsd-source"></a><span data-ttu-id="f71df-119">Pour générer un schéma à partir d'une source non XSD</span><span class="sxs-lookup"><span data-stu-id="f71df-119">To generate a schema from a non-XSD source</span></span>  
  
1.  <span data-ttu-id="f71df-120">Dans **l’Explorateur de solutions**, avec le bouton droit à un projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="f71df-120">In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="f71df-121">Dans le **ajouter les éléments générés - \< *BizTalk ProjectName* \>**  boîte de dialogue le **modèles** , cliquez sur **générer Schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f71df-121">In the **Add Generated Items - \<*BizTalk ProjectName*\>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="f71df-122">Dans le **générer les schémas** boîte de dialogue le **type de Document** la liste déroulante, sélectionnez **schéma XDR**, **DTD schéma**, ou **XML bien formé**.</span><span class="sxs-lookup"><span data-stu-id="f71df-122">In the **Generate Schemas** dialog box, in the **Document type** drop-down list, select **XDR Schema**, **DTD Schema**, or **Well-Formed XML**.</span></span>  
  
     <span data-ttu-id="f71df-123">Si vous consultez une **DTD (non chargé)** ou **XML bien formé (non chargé)** dans la liste déroulante, sélectionnez le type de document approprié malgré tout, et vous serez guidé dans le processus d’installation de le DLL manquante.</span><span class="sxs-lookup"><span data-stu-id="f71df-123">If you see either **DTD (Not Loaded)** or **Well-Formed XML (Not Loaded)** in the drop-down list, select the appropriate document type anyway, and you will be guided through the process of installing the missing DLL.</span></span> <span data-ttu-id="f71df-124">Répétez ensuite ces étapes.</span><span class="sxs-lookup"><span data-stu-id="f71df-124">Then repeat these steps.</span></span>  
  
4.  <span data-ttu-id="f71df-125">Dans le **générer les schémas** boîte de dialogue, cliquez sur **Parcourir**, recherchez le fichier que vous souhaitez importer, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f71df-125">In the **Generate Schemas** dialog box, click **Browse**, locate the file you want to import, and then click **Open**.</span></span> <span data-ttu-id="f71df-126">Le fichier localisé doit correspondre au type de document que vous avez sélectionné à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="f71df-126">The file you locate must match the document type you selected in the previous step.</span></span>  
  
     <span data-ttu-id="f71df-127">Un nouveau schéma est généré à partir du fichier spécifié. Il porte le même nom que ce fichier ainsi que l'extension .xsd et est ouvert dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f71df-127">A new schema is generated from the specified file, using the same name as that file with the .xsd extension, and opened in BizTalk Editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71df-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f71df-128">See Also</span></span>  
 [<span data-ttu-id="f71df-129">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="f71df-129">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)