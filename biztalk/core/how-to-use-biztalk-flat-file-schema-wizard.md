---
title: "Comment utiliser l’Assistant schéma de fichier plat BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cb8b18-266d-422e-bdb8-1efefb6b4c8e
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff7d87959bd39b9040a495022c2b7bf352954848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-biztalk-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-102">Utilisation de l'Assistant Schéma de fichier plat BizTalk</span><span class="sxs-lookup"><span data-stu-id="9abd1-102">How to Use BizTalk Flat File Schema Wizard</span></span>
<span data-ttu-id="9abd1-103">Dans les versions précédentes de BizTalk Server, vous deviez ajouter manuellement les annotations aux schémas XSD (XML Schema Definition language) dans l'Éditeur de schéma BizTalk pour rendre ces schémas compréhensibles par les composants de pipeline de fichier plat, tels que Désassembleur de fichier plat et Assembleur de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="9abd1-103">In previous releases of BizTalk Server, you had to manually add the annotations to XML Schema Definition language (XSD) schemas in the BizTalk Schema Editor to make these schemas understandable to Flat File Pipeline components, such as Flat File Disassembler and Flat File Assembler.</span></span> <span data-ttu-id="9abd1-104">Vous pouvez toujours procéder de cette manière à l'aide de l'Éditeur de schéma [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9abd1-104">You can still do this using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Schema Editor.</span></span> <span data-ttu-id="9abd1-105">Pour réduire le nombre d'étapes manuelles et accélérer la création de solutions, utilisez l'Assistant Schéma de fichier plat BizTalk, qui offre les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="9abd1-105">To reduce the number of manual steps and time needed to create solutions, you use the BizTalk Flat File Schema Wizard, which provides the following functionalities:</span></span>  
  
-   <span data-ttu-id="9abd1-106">utilisation d'instances de fichier plat réelles comme entrées ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-106">Uses real flat file instances as input.</span></span>  
  
-   <span data-ttu-id="9abd1-107">surface de conception visuelle pour le traitement des schémas de fichier plat délimité et positionnel ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-107">Includes a visual design surface for working with delimited and positional flat file schemas.</span></span>  
  
-   <span data-ttu-id="9abd1-108">processus réentrant basé sur un Assistant permettant d'ajouter des éléments au schéma et de définir des annotations associées au fichier plat de manière interactive ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-108">Uses a re-entrant wizard-based process for adding elements to the schema and defining flat file related annotations interactively.</span></span>  
  
-   <span data-ttu-id="9abd1-109">prise en charge des identificateurs de balise et des délimiteurs sous forme de caractère et de valeur hexadécimale ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-109">Provides support for tag identifiers and character and hexadecimal delimiters.</span></span>  
  
-   <span data-ttu-id="9abd1-110">détermination automatique des décalages d'identificateur de balise et de l'ordre de délimitation des enfants ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-110">Automatically determines tag identifier offsets and child delimiting order.</span></span>  
  
-   <span data-ttu-id="9abd1-111">fonctions de prévisualisation pour le format de fichier ;</span><span class="sxs-lookup"><span data-stu-id="9abd1-111">Provides preview capabilities for the file format.</span></span>  
  
-   <span data-ttu-id="9abd1-112">possibilité de sélectionner les sous-données privilégiées dans l'instance d'échange à utiliser pour définir les schémas de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="9abd1-112">Enables you to select preferred sub-data within the interchange instance to use to define the flat file schemas.</span></span>  
  
## <a name="how-to-start-the-biztalk-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-113">Démarrage de l'Assistant Schéma de fichier plat BizTalk</span><span class="sxs-lookup"><span data-stu-id="9abd1-113">How to Start the BizTalk Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-114">Vous pouvez démarrer l'Assistant à partir de l'Explorateur de solutions Microsoft Visual Studio ou de l'Éditeur de schéma BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9abd1-114">You can start the wizard from either the Microsoft Visual Studio Solution Explorer or from the BizTalk Schema Editor.</span></span>  
  
#### <a name="to-start-the-wizard-from-solution-explorer"></a><span data-ttu-id="9abd1-115">Pour démarrer l'Assistant à partir de l'Explorateur de solutions</span><span class="sxs-lookup"><span data-stu-id="9abd1-115">To start the wizard from Solution Explorer</span></span>  
  
1.  <span data-ttu-id="9abd1-116">Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-116">In Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="9abd1-117">Pour ajouter le nouveau schéma de fichier plat, cliquez sur le projet BizTalk, puis sélectionnez **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-117">To add the new flat-file schema, right-click the BizTalk project, and select **Add**.</span></span>  
  
3.  <span data-ttu-id="9abd1-118">Cliquez sur **un nouvel élément.**</span><span class="sxs-lookup"><span data-stu-id="9abd1-118">Click **New Item.**</span></span>  
  
     <span data-ttu-id="9abd1-119">![Menu de l’Explorateur de solutions](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")</span><span class="sxs-lookup"><span data-stu-id="9abd1-119">![Solution Explorer menu](../core/media/flatfileschemawizard-01.gif "FlatFileSchemaWizard_01")</span></span>  
  
4.  <span data-ttu-id="9abd1-120">Dans le **ajouter un nouvel élément** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9abd1-120">In the **Add New Item** window, do the following:</span></span>  
  
    1.  <span data-ttu-id="9abd1-121">Dans le **catégories** section, sélectionnez **les fichiers de schéma**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-121">In the **Categories** section, select **Schema Files**.</span></span>  
  
    2.  <span data-ttu-id="9abd1-122">Dans le **modèles** section, sélectionnez **Assistant schéma de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-122">In the **Templates** section, select **Flat File Schema Wizard**.</span></span>  
  
    3.  <span data-ttu-id="9abd1-123">Dans le **nom** zone de texte, tapez un nom pour le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="9abd1-123">In the **Name** text box, type a name for the new schema.</span></span>  
  
    4.  <span data-ttu-id="9abd1-124">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-124">Click **Add**.</span></span>  
  
         <span data-ttu-id="9abd1-125">L'Assistant Schéma de fichier plat BizTalk s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="9abd1-125">The BizTalk Flat File Schema Wizard opens.</span></span>  
  
#### <a name="to-start-the-wizard-from-the-schema-editor"></a><span data-ttu-id="9abd1-126">Pour démarrer l'Assistant à partir de l'Éditeur de schéma</span><span class="sxs-lookup"><span data-stu-id="9abd1-126">To start the Wizard from the Schema Editor</span></span>  
  
1.  <span data-ttu-id="9abd1-127">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-127">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="9abd1-128">Pour ajouter le nouveau schéma de fichier plat, cliquez sur le projet BizTalk, puis sélectionnez **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-128">To add the new flat-file schema, right-click the BizTalk project, and select **Add**.</span></span> <span data-ttu-id="9abd1-129">Sélectionnez **un nouvel élément** et cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-129">Select **New Item** and click **New Item**.</span></span>  
  
3.  <span data-ttu-id="9abd1-130">Dans le **ajouter un nouvel élément** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9abd1-130">In the **Add New Item** window, do the following:</span></span>  
  
    1.  <span data-ttu-id="9abd1-131">Dans le **catégories** section, sélectionnez **les fichiers de schéma**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-131">In the **Categories** section, select **Schema Files**.</span></span>  
  
    2.  <span data-ttu-id="9abd1-132">Dans le **modèles** section, sélectionnez **schéma de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-132">In the **Templates** section, select **Flat File Schema**.</span></span>  
  
    3.  <span data-ttu-id="9abd1-133">Dans le **nom** zone de texte, tapez un nom pour le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="9abd1-133">In the **Name** text box, type a name for the new schema.</span></span>  
  
    4.  <span data-ttu-id="9abd1-134">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-134">Click **Add**.</span></span>  
  
    5.  <span data-ttu-id="9abd1-135">Avec le bouton droit **racine** et sélectionnez **définir l’enregistrement à partir de l’Instance de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-135">Right-click **Root** and select **Define Record from Flat File Instance**.</span></span>  
  
         <span data-ttu-id="9abd1-136">L'Assistant Schéma de fichier plat BizTalk démarre.</span><span class="sxs-lookup"><span data-stu-id="9abd1-136">The BizTalk Flat File Schema Wizard now starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9abd1-137">Si vous avez un schéma de travail est ouvert dans l’éditeur de schéma, vous devez simplement est droit sur le nœud sélectionné, puis sélectionnez **définir l’enregistrement à partir de l’Instance de fichier plat**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-137">If you have a working schema opened in the Schema Editor, all you need to do is right-click the selected node and then select **Define Record from Flat File Instance**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9abd1-138">Le **définir l’enregistrement à partir de l’Instance de fichier plat** option est activée si le nœud sélectionné est un enregistrement sans éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="9abd1-138">The **Define Record from Flat File Instance** option is enabled if the selected node is a record without child elements.</span></span> <span data-ttu-id="9abd1-139">Si le nœud sélectionné comporte des éléments enfants, l'Assistant supprime tous les éléments enfants actuels et en crée de nouveaux.</span><span class="sxs-lookup"><span data-stu-id="9abd1-139">If the selected node has child elements, the wizard deletes all current child elements and generates the new ones.</span></span> <span data-ttu-id="9abd1-140">L'Assistant vous invite à confirmer la suppression des éléments enfants existants.</span><span class="sxs-lookup"><span data-stu-id="9abd1-140">The wizard prompts you to confirm before deleting the existing child elements.</span></span>  
  
## <a name="considerations-for-using-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-141">Éléments à prendre en compte lors de l'utilisation de l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-141">Considerations for Using the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-142">Cette section décrit les problèmes à prendre en compte lors de l'utilisation de l'Assistant Schéma de fichier plat BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9abd1-142">This section describes issues you should consider when working with the BizTalk Flat File Schema Wizard.</span></span>  
  
### <a name="working-with-multibyte-character-set-mbcs"></a><span data-ttu-id="9abd1-143">Utilisation du jeu de caractères multi-octets (MBCS)</span><span class="sxs-lookup"><span data-stu-id="9abd1-143">Working with Multibyte Character Set (MBCS)</span></span>  
 <span data-ttu-id="9abd1-144">Par défaut, le **compter les positions par octet** case à cocher est désactivée sur l’écran d’informations de schéma de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="9abd1-144">By default, the **Count positions in bytes** check box is unchecked on the Flat File Schema Information screen.</span></span> <span data-ttu-id="9abd1-145">L'Assistant compte les positions par caractère, ce qui signifie que si votre instance de fichier plat positionnel comporte des caractères MBCS, les positions ne sont pas comptées correctement.</span><span class="sxs-lookup"><span data-stu-id="9abd1-145">The wizard counts the positions by characters; which mean that if you have MBCS characters in your positional flat file instance, the positions are not counted correctly.</span></span> <span data-ttu-id="9abd1-146">En sélectionnant le **compter les positions par octet** case à cocher, l’Assistant affiche les caractères MBCS avec une indication supplémentaire de leur longueur positionnelle.</span><span class="sxs-lookup"><span data-stu-id="9abd1-146">By selecting the **Count positions in bytes** check box, the wizard displays MBCS characters with an additional indication of their positional length.</span></span> <span data-ttu-id="9abd1-147">Le caractère occupe une position sur l'affichage et la longueur restante est remplie par des points « • ».</span><span class="sxs-lookup"><span data-stu-id="9abd1-147">The character takes one position on the display and the remaining length is filled out with dot symbols, “•”.</span></span> <span data-ttu-id="9abd1-148">Le nombre de symboles point remplis sera défini en fonction des fichiers enregistrés dans le format du jeu de caractères codés sur deux octets (DBCS), Unicode ou UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9abd1-148">The number of dot symbols filled will be depending on the files that were saved in double byte character set (DBCS), Unicode or UTF-8 format.</span></span>  
  
### <a name="code-pages-supported-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-149">Pages de codes prises en charge dans l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-149">Code Pages Supported in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-150">Les pages de codes prises en charge par l'Assistant sont listées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9abd1-150">The following is a list of supported code pages for the wizard:</span></span>  
  
-   <span data-ttu-id="9abd1-151">Arabe (1256)</span><span class="sxs-lookup"><span data-stu-id="9abd1-151">Arabic (1256)</span></span>  
  
-   <span data-ttu-id="9abd1-152">ASCII (20127)</span><span class="sxs-lookup"><span data-stu-id="9abd1-152">ASCII (20127)</span></span>  
  
-   <span data-ttu-id="9abd1-153">Baltique (1257)</span><span class="sxs-lookup"><span data-stu-id="9abd1-153">Baltic (1257)</span></span>  
  
-   <span data-ttu-id="9abd1-154">Big-Endian-UTF16 (1201)</span><span class="sxs-lookup"><span data-stu-id="9abd1-154">Big-Endian-UTF16 (1201)</span></span>  
  
-   <span data-ttu-id="9abd1-155">Europe centrale (1250)</span><span class="sxs-lookup"><span data-stu-id="9abd1-155">Central-European (1250)</span></span>  
  
-   <span data-ttu-id="9abd1-156">Cyrillique (1251)</span><span class="sxs-lookup"><span data-stu-id="9abd1-156">Cyrillic (1251)</span></span>  
  
-   <span data-ttu-id="9abd1-157">Grec (1253)</span><span class="sxs-lookup"><span data-stu-id="9abd1-157">Greek (1253)</span></span>  
  
-   <span data-ttu-id="9abd1-158">Hébreu (1255)</span><span class="sxs-lookup"><span data-stu-id="9abd1-158">Hebrew (1255)</span></span>  
  
-   <span data-ttu-id="9abd1-159">Japonais-Shift-JIS (932)</span><span class="sxs-lookup"><span data-stu-id="9abd1-159">Japanese-Shift-JIS (932)</span></span>  
  
-   <span data-ttu-id="9abd1-160">Coréen (949)</span><span class="sxs-lookup"><span data-stu-id="9abd1-160">Korean (949)</span></span>  
  
-   <span data-ttu-id="9abd1-161">Little-Endian-UTF16 (1200)</span><span class="sxs-lookup"><span data-stu-id="9abd1-161">Little-Endian-UTF16 (1200)</span></span>  
  
-   <span data-ttu-id="9abd1-162">Chinois simplifié GBK (936)</span><span class="sxs-lookup"><span data-stu-id="9abd1-162">Simplified-Chinese-GBK (936)</span></span>  
  
-   <span data-ttu-id="9abd1-163">Chinois simplifié GB18030 (54936)</span><span class="sxs-lookup"><span data-stu-id="9abd1-163">Simplified-Chinese-GB18030 (54936)</span></span>  
  
-   <span data-ttu-id="9abd1-164">Thaï (874)</span><span class="sxs-lookup"><span data-stu-id="9abd1-164">Thai (874)</span></span>  
  
-   <span data-ttu-id="9abd1-165">Chinois traditionnel BIG5 (950)</span><span class="sxs-lookup"><span data-stu-id="9abd1-165">Traditional-Chinese-BIG5 (950)</span></span>  
  
-   <span data-ttu-id="9abd1-166">Turc (1254)</span><span class="sxs-lookup"><span data-stu-id="9abd1-166">Turkish (1254)</span></span>  
  
-   <span data-ttu-id="9abd1-167">UTF-7 (65000)</span><span class="sxs-lookup"><span data-stu-id="9abd1-167">UTF-7 (65000)</span></span>  
  
-   <span data-ttu-id="9abd1-168">UTF-8 (65001)</span><span class="sxs-lookup"><span data-stu-id="9abd1-168">UTF-8 (65001)</span></span>  
  
-   <span data-ttu-id="9abd1-169">Vietnamien (1258)</span><span class="sxs-lookup"><span data-stu-id="9abd1-169">Vietnamese (1258)</span></span>  
  
-   <span data-ttu-id="9abd1-170">Europe occidentale (1252)</span><span class="sxs-lookup"><span data-stu-id="9abd1-170">Western-European (1252)</span></span>  
  
### <a name="record-types-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-171">Types d'enregistrement dans l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-171">Record Types in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-172">Les fichiers plats ne peuvent pas contenir d'enregistrements délimités à l'intérieur d'enregistrements positionnels.</span><span class="sxs-lookup"><span data-stu-id="9abd1-172">Flat files cannot contain delimited records within positional records.</span></span> <span data-ttu-id="9abd1-173">L’Assistant étant réentrant basé, les cases d’option qui définissent le type de la **par symbole délimiteur** et **par positions relatives** sont activées ou désactivées selon le format des enregistrements parents pour l’enfant que vous définissez dans l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="9abd1-173">Because the wizard is re-entrant based, the radio buttons that define the type of the **By delimiter symbol** and **By relative positions** are enabled or disabled based on the format of the parent records for the child which you define in the wizard.</span></span> <span data-ttu-id="9abd1-174">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9abd1-174">For example,</span></span>  
  
-   <span data-ttu-id="9abd1-175">Si l'Assistant est exécuté pour un enfant d'un enregistrement délimité, les deux cases d'option sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="9abd1-175">If the wizard is run for a child of a delimited record, both radio buttons are selected.</span></span>  
  
-   <span data-ttu-id="9abd1-176">Si l’Assistant est exécuté pour un enfant d’un enregistrement positionnel, la **par symbole délimiteur** case d’option est désactivée.</span><span class="sxs-lookup"><span data-stu-id="9abd1-176">If the wizard is run for a child of a positional record, the **By delimiter symbol** radio button is cleared.</span></span>  
  
### <a name="delimiter-symbols-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-177">Symboles délimiteurs dans l'Assistant Fichier de schéma plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-177">Delimiter Symbols in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-178">La liste déroulante des propriétés de délimiteur enfant contient les délimiteurs communs suivants :</span><span class="sxs-lookup"><span data-stu-id="9abd1-178">The child delimiter property drop-down list contains with the following common delimiters:</span></span>  
  
-   <span data-ttu-id="9abd1-179">{CR}{LF}</span><span class="sxs-lookup"><span data-stu-id="9abd1-179">{CR}{LF}</span></span>  
  
-   <span data-ttu-id="9abd1-180">{CR}</span><span class="sxs-lookup"><span data-stu-id="9abd1-180">{CR}</span></span>  
  
-   <span data-ttu-id="9abd1-181">{LF}</span><span class="sxs-lookup"><span data-stu-id="9abd1-181">{LF}</span></span>  
  
-   <span data-ttu-id="9abd1-182">{TAB}</span><span class="sxs-lookup"><span data-stu-id="9abd1-182">{TAB}</span></span>  
  
-   <span data-ttu-id="9abd1-183">{ESPACE}</span><span class="sxs-lookup"><span data-stu-id="9abd1-183">{SPACE}</span></span>  
  
-   <span data-ttu-id="9abd1-184">{0x1A}</span><span class="sxs-lookup"><span data-stu-id="9abd1-184">{0x1A}</span></span>  
  
-   <span data-ttu-id="9abd1-185">&#124;</span><span class="sxs-lookup"><span data-stu-id="9abd1-185">&#124;</span></span>  
  
-   <span data-ttu-id="9abd1-186">,</span><span class="sxs-lookup"><span data-stu-id="9abd1-186">,</span></span>  
  
-   <span data-ttu-id="9abd1-187">;</span><span class="sxs-lookup"><span data-stu-id="9abd1-187">;</span></span>  
  
 <span data-ttu-id="9abd1-188">La valeur par défaut pour cette propriété est {CR}{LF}.</span><span class="sxs-lookup"><span data-stu-id="9abd1-188">The default value for this property is {CR}{LF}.</span></span> <span data-ttu-id="9abd1-189">La propriété est également une zone de texte modifiable, qui vous permet de spécifier le délimiteur enfant en tant que séquence de caractères ou comme valeurs hexadécimales des caractères.</span><span class="sxs-lookup"><span data-stu-id="9abd1-189">The property is also an editable text box, so that you can specify the child delimiter as a sequence of characters or as hexadecimal values of the characters.</span></span> <span data-ttu-id="9abd1-190">« une » ou « rue » sont des exemples d'utilisation de caractères pour le délimiteur enfant.</span><span class="sxs-lookup"><span data-stu-id="9abd1-190">An example of using characters for the child delimiter would be "a" or "street."</span></span> <span data-ttu-id="9abd1-191">Les délimiteurs hexadécimaux sont spécifiés selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="9abd1-191">Hexadecimal delimiters are specified using the following format:</span></span>  
  
-   <span data-ttu-id="9abd1-192">{0xnnnn} :</span><span class="sxs-lookup"><span data-stu-id="9abd1-192">{0xnnnn}.</span></span> <span data-ttu-id="9abd1-193">par exemple, {0x0D}{0x0A}, {0x09} ou {0x20}.</span><span class="sxs-lookup"><span data-stu-id="9abd1-193">For example, {0x0D}{0x0A}, {0x09} or {0x20}.</span></span>  
  
 <span data-ttu-id="9abd1-194">Voici un exemple d'utilisation de séquence de valeurs hexadécimales : {0x0D}{0x0A}, {0x09}{0x20}.</span><span class="sxs-lookup"><span data-stu-id="9abd1-194">An example of using sequence of hexadecimal values is {0x0D}{0x0A}, {0x09}{0x20}.</span></span>  
  
 <span data-ttu-id="9abd1-195">Si vous utilisez les symboles \\, {, ou} comme délimiteur, vous devez placer un symbole de barre oblique inverse supplémentaire devant le symbole de délimiteur, sinon vous recevrez un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9abd1-195">If you use the symbols \\, {, or } as the delimiter, you must place an additional backslash symbol in front of the delimiter symbol, otherwise you will receive an error message.</span></span> <span data-ttu-id="9abd1-196">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9abd1-196">For example,</span></span>  
  
-   <span data-ttu-id="9abd1-197">\\\\, \\{, ou \\}.</span><span class="sxs-lookup"><span data-stu-id="9abd1-197">\\\\, \\{, or \\}.</span></span>  
  
### <a name="relative-positions-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-198">Positions relatives dans l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-198">Relative Positions in the Flat File Schema Wizard</span></span>  
  
#### <a name="setting-position-markers"></a><span data-ttu-id="9abd1-199">Définition des marqueurs de position</span><span class="sxs-lookup"><span data-stu-id="9abd1-199">Setting Position Markers</span></span>  
 <span data-ttu-id="9abd1-200">Cliquez sur un marqueur de position dans la zone de sélection de la position pour déterminer la nouvelle ligne de marqueur de position.</span><span class="sxs-lookup"><span data-stu-id="9abd1-200">Use the left mouse button to click a position marker in the position selection box to set the new position marker line.</span></span> <span data-ttu-id="9abd1-201">Le marqueur de position est représenté sous la forme d'un trait plein.</span><span class="sxs-lookup"><span data-stu-id="9abd1-201">The position marker is represented as a solid line.</span></span> <span data-ttu-id="9abd1-202">Par défaut, une ligne de marqueur de position figure au début de l'enregistrement à la position zéro.</span><span class="sxs-lookup"><span data-stu-id="9abd1-202">By default, a position marker line exists at the beginning of the record at position zero.</span></span> <span data-ttu-id="9abd1-203">Pour supprimer une ligne de marqueur de position existante, cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="9abd1-203">To remove an existing position marker line, use the left mouse button to click  it.</span></span>  
  
### <a name="escape-characters-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-204">Caractères d'échappement dans l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-204">Escape Characters in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-205">Un caractère d'échappement est un caractère unique qui supprime toute signification du caractère qui le suit.</span><span class="sxs-lookup"><span data-stu-id="9abd1-205">An escape character is a single character that suppresses any special meaning of the character that follows it.</span></span> <span data-ttu-id="9abd1-206">Pour plus d’informations, consultez [caractères d’échappement](../core/escape-characters.md) rubrique sous [comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span><span class="sxs-lookup"><span data-stu-id="9abd1-206">For more information, see [Escape Characters](../core/escape-characters.md) topic under [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span></span> <span data-ttu-id="9abd1-207">Vous utilisez la propriété de caractère d'échappement dans l'Assistant pour indiquer le caractère d'échappement à utiliser lors de l'analyse de l'instance de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="9abd1-207">You use the escape character property in the wizard to specify the escape character to use when parsing the flat file instance.</span></span> <span data-ttu-id="9abd1-208">La valeur par défaut est Null, ce qui signifie que le caractère d'échappement par défaut défini au niveau du schéma est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9abd1-208">The default is null, meaning that the default escape character defined at the schema level is used.</span></span>  
  
 <span data-ttu-id="9abd1-209">Le caractère d'échappement peut être spécifié sous forme de caractère ou de valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="9abd1-209">The escape character can be specified as a character or as a hexadecimal value.</span></span> <span data-ttu-id="9abd1-210">La valeur hexadécimale est indiquée selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="9abd1-210">The hexadecimal value is specified using the following format:</span></span>  
  
-   <span data-ttu-id="9abd1-211">{0xnnnn} :</span><span class="sxs-lookup"><span data-stu-id="9abd1-211">{0xnnnn}.</span></span> <span data-ttu-id="9abd1-212">par exemple, {0x0D}{0x0A}, {0x09} ou {0x20}</span><span class="sxs-lookup"><span data-stu-id="9abd1-212">For example, {0x0D}{0x0A}, {0x09}, or {0x20}.</span></span>  
  
 <span data-ttu-id="9abd1-213">Si vous utilisez les symboles \\, {, ou} comme caractère d’échappement, vous devez placer un symbole de barre oblique inverse supplémentaire devant le symbole de délimiteur, sinon vous recevrez un message d’erreur, par exemple,</span><span class="sxs-lookup"><span data-stu-id="9abd1-213">If you use the symbols \\, {, or } as the escape character, you must place an additional backslash symbol in front of the delimiter symbol, otherwise you will receive an error message For example,</span></span>  
  
-   <span data-ttu-id="9abd1-214">\\\\, \\{, \\}.</span><span class="sxs-lookup"><span data-stu-id="9abd1-214">\\\\, \\{, \\}.</span></span>  
  
### <a name="child-elements-in-the-flat-file-schema-wizard"></a><span data-ttu-id="9abd1-215">Éléments enfants dans l'Assistant Schéma de fichier plat</span><span class="sxs-lookup"><span data-stu-id="9abd1-215">Child Elements in the Flat File Schema Wizard</span></span>  
 <span data-ttu-id="9abd1-216">Chaque élément enfant contient **nom de l’élément**, **le Type d’élément**, **Type de données** et **contenu**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-216">Each child element contains **Element Name**, **Element Type**, **Data Type** and **Content**.</span></span> <span data-ttu-id="9abd1-217">Vous utilisez la **nom de l’élément** zone de texte, tapez un nom explicite pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="9abd1-217">You use the **Element Name** text box to type a meaningful name for the node.</span></span> <span data-ttu-id="9abd1-218">Le **le Type d’élément** est une liste déroulante avec les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="9abd1-218">The **Element Type** is a drop-down list with the following values:</span></span>  
  
-   <span data-ttu-id="9abd1-219">**Élément de champ**: Spécifie que ce nœud sera créé dans le schéma en tant qu’élément.</span><span class="sxs-lookup"><span data-stu-id="9abd1-219">**Field element**: Specifies that this node will be created in the schema as an element.</span></span>  
  
-   <span data-ttu-id="9abd1-220">**Attribut de champ**: Spécifie que ce nœud sera créé dans le schéma en tant qu’attribut.</span><span class="sxs-lookup"><span data-stu-id="9abd1-220">**Field attribute**: Specifies that this node will be created in the schema as an attribute.</span></span>  
  
-   <span data-ttu-id="9abd1-221">**Enregistrement**: Spécifie qu’un enregistrement sans enfants sera créé dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="9abd1-221">**Record**: Specifies that a record without children will be created in the schema.</span></span>  
  
-   <span data-ttu-id="9abd1-222">**Enregistrement répété**: Spécifie qu’un enregistrement sans enfants sera créé dans le schéma et son occurrence maximale est définie sur **Unbounded**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-222">**Repeating record**: Specifies that a record without children will be created in the schema and its max occurrence is set to **Unbounded**.</span></span>  
  
-   <span data-ttu-id="9abd1-223">**Ignorer**: rien ne sera créé dans le schéma de ce nœud.</span><span class="sxs-lookup"><span data-stu-id="9abd1-223">**Ignore**: Nothing will be created in the schema for this node.</span></span>  
  
 <span data-ttu-id="9abd1-224">Par défaut, tous les éléments sont de type **fieldelement** et leur type de données est **chaîne**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-224">By default all elements are of type **Field element** and their data type is **string**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9abd1-225">Un élément enfant peut être déclaré comme un **attribut de champ** uniquement s’il n’existe pas d’enfants avant qu’il qui sont déclarés comme **champ éléments**, **enregistrement** ou  **Enregistrement répété**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-225">A child element can be declared as a **Field attribute** only if there are no children before it that are declared as **Field elements**, **Record** or **Repeating record**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9abd1-226">Vous verrez un point d’exclamation devant le **nœuds enfants** dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="9abd1-226">You will see an exclamation mark in front of the **child nodes** in the following instances:</span></span>  
  
-   <span data-ttu-id="9abd1-227">Le **attribut de champ** est défini après **fieldelement**, **enregistrement,** ou **enregistrement répété**.</span><span class="sxs-lookup"><span data-stu-id="9abd1-227">The **Field attribute** is defined after **Field element**, **Record,** or **Repeating record**.</span></span>  
  
-   <span data-ttu-id="9abd1-228">L'élément enfant n'a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="9abd1-228">The child element does not have a name.</span></span>  
  
-   <span data-ttu-id="9abd1-229">L'élément enfant a un nom en double.</span><span class="sxs-lookup"><span data-stu-id="9abd1-229">The child element has a duplicate name.</span></span>  
  
-   <span data-ttu-id="9abd1-230">Le type de données sélectionné pour l'élément enfant n'est pas adapté au contenu.</span><span class="sxs-lookup"><span data-stu-id="9abd1-230">The selected data type for the child element is not suitable for the content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd1-231">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9abd1-231">See Also</span></span>  
 [<span data-ttu-id="9abd1-232">Description de l’Assistant schéma fichier plat BizTalk</span><span class="sxs-lookup"><span data-stu-id="9abd1-232">BizTalk Flat File Schema Wizard Walkthrough</span></span>](../core/biztalk-flat-file-schema-wizard-walkthrough.md)