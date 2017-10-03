---
title: "Configuration de jeu de caractères et séparateurs (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6249f2e1-70b0-4960-bbc4-0c3fefd26faa
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43e32c4d9a240c3302126fc403d64efd787ed54c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-charset-and-separators-x12"></a><span data-ttu-id="d2c72-102">Configuration du jeu de caractères et des séparateurs (X12)</span><span class="sxs-lookup"><span data-stu-id="d2c72-102">Configuring Charset and Separators (X12)</span></span>
<span data-ttu-id="d2c72-103">Dans l'accord de partenariat, vous pouvez spécifier le jeu de caractères utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour valider les propriétés de tiers lors de la création de l'enveloppe pour un message X12 sortant.</span><span class="sxs-lookup"><span data-stu-id="d2c72-103">In the partner agreement, you can specify the character set that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to validate party properties when creating the envelope for an outgoing X12 message.</span></span> <span data-ttu-id="d2c72-104">Vous pouvez également spécifier les séparateurs et terminateurs utilisés pour les segments dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="d2c72-104">You can also specify what separators and terminators will be used for the segments in the interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2c72-105">Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.</span><span class="sxs-lookup"><span data-stu-id="d2c72-105">The settings described here also apply to HIPAA interchanges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2c72-106">Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="d2c72-106">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="d2c72-107">**Élément de données**</span><span class="sxs-lookup"><span data-stu-id="d2c72-107">**Data element**</span></span>  
> -   <span data-ttu-id="d2c72-108">**Séparateur d’éléments composites (ISA16)**</span><span class="sxs-lookup"><span data-stu-id="d2c72-108">**Component element separator (ISA16)**</span></span>  
> -   <span data-ttu-id="d2c72-109">**Terminateur de segment**</span><span class="sxs-lookup"><span data-stu-id="d2c72-109">**Segment terminator**</span></span>  
> -   <span data-ttu-id="d2c72-110">**Suffixe**</span><span class="sxs-lookup"><span data-stu-id="d2c72-110">**Suffix**</span></span>  
> -   <span data-ttu-id="d2c72-111">**Remplacer les séparateurs dans la charge par**</span><span class="sxs-lookup"><span data-stu-id="d2c72-111">**Replace separators in payload with**</span></span>  
>   
>  <span data-ttu-id="d2c72-112">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="d2c72-112">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="d2c72-113">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="d2c72-113">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2c72-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d2c72-114">Prerequisites</span></span>  
 <span data-ttu-id="d2c72-115">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2c72-115">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-character-set-and-separators"></a><span data-ttu-id="d2c72-116">Pour configurer le jeu de caractères et les séparateurs</span><span class="sxs-lookup"><span data-stu-id="d2c72-116">To configure the character set and separators</span></span>  
  
1.  <span data-ttu-id="d2c72-117">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="d2c72-117">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="d2c72-118">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d2c72-118">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d2c72-119">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **jeu de caractères et séparateurs**.</span><span class="sxs-lookup"><span data-stu-id="d2c72-119">On a one-way agreement tab, under **Interchange Settings** section, click **Charset and Separators**.</span></span>  
  
3.  <span data-ttu-id="d2c72-120">À partir de la **du jeu de caractères à utiliser** liste déroulante, sélectionnez le X12 jeu de caractères à être utilisé pour valider les propriétés que vous entrez pour l’accord.</span><span class="sxs-lookup"><span data-stu-id="d2c72-120">From the **Character set to be used** drop-down list, select the X12 character set to be used to validate the properties that you enter for the agreement.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d2c72-121"> utilise uniquement ce paramètre pour valider les valeurs entrées pour les propriétés de l'accord correspondant.</span><span class="sxs-lookup"><span data-stu-id="d2c72-121"> only uses this setting to validate the values entered for the related agreement properties.</span></span> <span data-ttu-id="d2c72-122">Le pipeline d'envoi ou de réception ignore cette propriété de jeu de caractères lors de l'exécution du traitement.</span><span class="sxs-lookup"><span data-stu-id="d2c72-122">The receive pipeline or send pipeline will ignore this character-set property when performing run-time processing.</span></span>  
  
4.  <span data-ttu-id="d2c72-123">Pour **élément de données**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données composites consistant en deux ou plusieurs éléments de données simples et des éléments de données simples qui ne font pas partie d’un élément composite.</span><span class="sxs-lookup"><span data-stu-id="d2c72-123">For **Data element**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate composite data elements consisting of two or more simple data elements, and simple data elements that are not part of a composite element.</span></span> <span data-ttu-id="d2c72-124">Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="d2c72-124">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="d2c72-125">Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="d2c72-125">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
5.  <span data-ttu-id="d2c72-126">Pour **séparateur d’éléments composites (ISA16)**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données simples au sein d’éléments de données composites.</span><span class="sxs-lookup"><span data-stu-id="d2c72-126">For **Component element separator (ISA16)**, enter a single character that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to separate simple data elements within composite data elements.</span></span> <span data-ttu-id="d2c72-127">Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="d2c72-127">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="d2c72-128">Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="d2c72-128">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
6.  <span data-ttu-id="d2c72-129">Pour **terminateur de Segment**, entrez un caractère unique pour indiquer la fin d’un segment EDI.</span><span class="sxs-lookup"><span data-stu-id="d2c72-129">For **Segment terminator**, enter a single character to indicate the end of an EDI segment.</span></span> <span data-ttu-id="d2c72-130">Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="d2c72-130">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span>  
  
     <span data-ttu-id="d2c72-131">Si le type est **Char**, la valeur par défaut est  **~** .</span><span class="sxs-lookup"><span data-stu-id="d2c72-131">If the type is **Char**, the default value is **~**.</span></span>  
  
     <span data-ttu-id="d2c72-132">Si le type est **Hex**, la valeur par défaut est **7E**.</span><span class="sxs-lookup"><span data-stu-id="d2c72-132">If the type is **Hex**, the default value is **7E**.</span></span>  
  
     <span data-ttu-id="d2c72-133">Cet élément de données est requis.</span><span class="sxs-lookup"><span data-stu-id="d2c72-133">This data element is required.</span></span>  
  
     <span data-ttu-id="d2c72-134">Cet élément est limité aux valeurs du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="d2c72-134">This element is limited to the values in the ASCII character set.</span></span> <span data-ttu-id="d2c72-135">Cette propriété n'est pas validée par rapport au jeu de caractères X12 défini dans la page Général.</span><span class="sxs-lookup"><span data-stu-id="d2c72-135">This property is not validated against the X12 character set defined in the General page.</span></span>  
  
     <span data-ttu-id="d2c72-136">Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="d2c72-136">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
7.  <span data-ttu-id="d2c72-137">Pour **suffixe**, sélectionnez le caractère à utiliser **avec** la valeur du terminateur de Segment.</span><span class="sxs-lookup"><span data-stu-id="d2c72-137">For **Suffix**, select the character to use **with** the Segment Terminator value.</span></span> <span data-ttu-id="d2c72-138">Les options sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2c72-138">Options include:</span></span>  
  
    -   <span data-ttu-id="d2c72-139">**Aucun**: par défaut</span><span class="sxs-lookup"><span data-stu-id="d2c72-139">**None**: Default</span></span>  
  
    -   <span data-ttu-id="d2c72-140">**CR**: retour chariot</span><span class="sxs-lookup"><span data-stu-id="d2c72-140">**CR**: Carriage Return</span></span>  
  
    -   <span data-ttu-id="d2c72-141">**LF**: saut de ligne</span><span class="sxs-lookup"><span data-stu-id="d2c72-141">**LF**: Line Feed</span></span>  
  
    -   <span data-ttu-id="d2c72-142">**CR LF**: flux de retour de ligne de chariot</span><span class="sxs-lookup"><span data-stu-id="d2c72-142">**CR LF**: Carriage Return/Line Feed</span></span>  
  
     <span data-ttu-id="d2c72-143">Les combinaisons d’un terminateur de segment et d’un suffixe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2c72-143">The Segment Terminator and Suffix combinations include the following:</span></span>  
  
    -   <span data-ttu-id="d2c72-144">**N’importe quel** terminateur de Segment + **aucun** suffixe</span><span class="sxs-lookup"><span data-stu-id="d2c72-144">**Any** Segment Terminator + **None** Suffix</span></span>  
  
    -   <span data-ttu-id="d2c72-145">**N’importe quel** terminateur de Segment + **CR** suffixe</span><span class="sxs-lookup"><span data-stu-id="d2c72-145">**Any** Segment Terminator + **CR** Suffix</span></span>  
  
    -   <span data-ttu-id="d2c72-146">**N’importe quel** terminateur de Segment + **CR LF** suffixe</span><span class="sxs-lookup"><span data-stu-id="d2c72-146">**Any** Segment Terminator + **CR LF** Suffix</span></span>  
  
    -   <span data-ttu-id="d2c72-147">**D (Hex)** terminateur de Segment + **aucun** suffixe : cette combinaison agit comme si le terminateur de Segment est vide et suffixe est définie sur CR.</span><span class="sxs-lookup"><span data-stu-id="d2c72-147">**D (Hex)** Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to CR.</span></span>  
  
    -   <span data-ttu-id="d2c72-148">Un terminateur de Segment (Hex) + **aucun** suffixe : cette combinaison agit comme si le terminateur de Segment est vide et suffixe est définie sur LF.</span><span class="sxs-lookup"><span data-stu-id="d2c72-148">A (Hex) Segment Terminator + **None** Suffix: This combination behaves as if Segment Terminator is blank and Suffix is set to LF.</span></span>  
  
    -   <span data-ttu-id="d2c72-149">**D (Hex)** terminateur de Segment + **LF** suffixe : cette combinaison agit comme si le terminateur de Segment était CR et suffixe est défini sur LF.</span><span class="sxs-lookup"><span data-stu-id="d2c72-149">**D (Hex)** Segment Terminator + **LF** Suffix: This combination behaves as if Segment Terminator is CR and Suffix is set to LF.</span></span>  
  
8.  <span data-ttu-id="d2c72-150">Si les données de charge contient des caractères qui sont également utilisés comme séparateurs de données, segment ou composant, vérifiez **remplacer les séparateurs dans la charge utile avec** et spécifiez un caractère de remplacement.</span><span class="sxs-lookup"><span data-stu-id="d2c72-150">If the payload data contains characters that are also used as data, segment, or component separators, check **Replace separators in payload with** and specify a replacement character.</span></span> <span data-ttu-id="d2c72-151">Lors de la création du message X12 sortant, les instances des caractères de séparation dans les données de charge sont remplacées par le caractère spécifié.</span><span class="sxs-lookup"><span data-stu-id="d2c72-151">When generating the outbound X12 message, all instances of separator characters in the payload data will be replaced with the specified character.</span></span> <span data-ttu-id="d2c72-152">Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales.</span><span class="sxs-lookup"><span data-stu-id="d2c72-152">Select **Char** for a character data element or **Hex** for a hexadecimal data element.</span></span> <span data-ttu-id="d2c72-153">Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="d2c72-153">The character you entered will automatically change when you change the format from **Char** to **Hex** or vice-versa.</span></span>  
  
9. <span data-ttu-id="d2c72-154">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d2c72-154">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c72-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2c72-155">See Also</span></span>  
 [<span data-ttu-id="d2c72-156">Configuration des paramètres d’échange (X12)</span><span class="sxs-lookup"><span data-stu-id="d2c72-156">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)