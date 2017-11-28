---
title: Configuration du fichier XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52851901-8374-412f-9c29-83845d8d4861
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d791de9b6fe90ebb850874026e8d52e49732f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-xml-file"></a><span data-ttu-id="dae5b-102">Configuration du fichier XML</span><span class="sxs-lookup"><span data-stu-id="dae5b-102">Configuring the XML File</span></span>
<span data-ttu-id="dae5b-103">Lorsque vous installez l'authentification unique de l'entreprise, un fichier XML intitulé ENTSSO.xml est installé dans le répertoire Extensions.</span><span class="sxs-lookup"><span data-stu-id="dae5b-103">When you install Enterprise Single Sign-On (SSO), an XML file named ENTSSO.xml is installed in your Extensions directory.</span></span> <span data-ttu-id="dae5b-104">En modifiant ce fichier, vous définissez la configuration pour toutes les instances d'agent de gestion ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-104">By editing the file, you define the configuration for all instances of the ENTSSO Management Agent (MA).</span></span>  
  
 <span data-ttu-id="dae5b-105">Le fichier est semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="dae5b-105">The file is similar to the following:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<sso>  
  
  <SourceMA name="RACFMA1" objectType="person" attribute="uid"/>  
  <SourceMA name="ACF2" objectType="person" attribute="uid"/>  
  
  <ENTSSOMA name ="ENTSSOMA1" adma="ADMA1" deleteAll="true">  
    <Application name="AppForRACF1A" sourceMA="RACFMA1" create="true" delete="true"/>  
    <Application name="AppForRACF1B" sourceMA="RACFMA1" create="true" delete="false"/>  
  </ENTSSOMA>  
  
  <ENTSSOMA name ="ENTSSOMA2" adma="ADMA1" deleteAll="true">  
    <Application name="AppForACF2" sourceMA="ACF2"/>  
  </ENTSSOMA>  
  
</sso>  
```  
  
## <a name="xml-elements-and-attributes"></a><span data-ttu-id="dae5b-106">Éléments et attributs XML</span><span class="sxs-lookup"><span data-stu-id="dae5b-106">XML Elements and Attributes</span></span>  
 <span data-ttu-id="dae5b-107">La liste suivante répertorie les éléments et attributs que vous définissez dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="dae5b-107">The following list describes the elements and attributes that you define in the XML file.</span></span> <span data-ttu-id="dae5b-108">Notez que tous les noms des éléments et des attributs de ce fichier respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="dae5b-108">Note that all element and attribute names in this file are case sensitive.</span></span>  
  
 <span data-ttu-id="dae5b-109">**Élément : ENTSSO** -définit la configuration d’une seule instance de l’agent de gestion ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-109">**Element: ENTSSO** - Defines the configuration of a single ENTSSO MA instance.</span></span> <span data-ttu-id="dae5b-110">Plusieurs éléments ENTSSO sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dae5b-110">Multiple ENTSSO elements are allowed.</span></span>  
  
 <span data-ttu-id="dae5b-111">**Attribut : nom** - définit le nom de l’instance de l’Agent de gestion ENTSSO et doit correspondre au nom de l’instance de l’Agent de gestion ENTSSO dans Microsoft Identity Integration Server (MIIS).</span><span class="sxs-lookup"><span data-stu-id="dae5b-111">**Attribute: name** - Defines the instance name of the ENTSSO Management Agent, and must match the name of the ENTSSO Management Agent instance in Microsoft Identity Integration Server (MIIS).</span></span>  
  
 <span data-ttu-id="dae5b-112">**Attribut : adma** -définit le nom de l’instance de l’Agent de gestion Active Directory qui sera utilisé par cette instance de l’Agent de gestion ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-112">**Attribute: adma** - Defines the instance name of the Active Directory Management Agent that will be used by this ENTSSO Management Agent instance.</span></span> <span data-ttu-id="dae5b-113">L'agent de gestion Active Directory fournit le nom de domaine Windows et le nom d'utilisateur Windows pour le mappage.</span><span class="sxs-lookup"><span data-stu-id="dae5b-113">The Active Directory Management Agent provides the Windows domain name and Windows user name for the mapping.</span></span> <span data-ttu-id="dae5b-114">Le nom de cette instance d'agent de gestion Active Directory doit correspondre au nom d'une instance d'agent de gestion Active Directory dans MIIS.</span><span class="sxs-lookup"><span data-stu-id="dae5b-114">This Active Directory Management Agent instance name must match the name of an Active Directory Management Agent instance in MIIS.</span></span>  
  
 <span data-ttu-id="dae5b-115">**Attribut : deleteAll** - en option, valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-115">**Attribute: deleteAll** - Optional; default is `true`.</span></span> <span data-ttu-id="dae5b-116">S'il est défini sur `true` et qu'une identité Windows est supprimée, tous les mappages utilisant cette identité Windows sont supprimés des applications ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-116">If this is set to `true`, and a Windows identity is deleted, all mappings with that Windows identity are deleted from all ENTSSO applications.</span></span>  
  
 <span data-ttu-id="dae5b-117">**Élément : Application de** -définit la relation entre une application associée SSO et un Agent de gestion externe.</span><span class="sxs-lookup"><span data-stu-id="dae5b-117">**Element: Application** - Defines the relationship between an SSO affiliate application and an external Management Agent.</span></span> <span data-ttu-id="dae5b-118">Plusieurs éléments `Application` sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dae5b-118">Multiple `Application` elements are allowed.</span></span>  
  
 <span data-ttu-id="dae5b-119">**Attribut : nom** -définit le nom de l’application associée SSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-119">**Attribute: name** - Defines the name of the SSO affiliate application.</span></span> <span data-ttu-id="dae5b-120">Cette application doit déjà exister au sein du système ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="dae5b-120">This application must already exist within the ENTSSO system.</span></span>  
  
 <span data-ttu-id="dae5b-121">**Attribut : sourceMA** -définit le nom d’instance de la source (externe) de l’Agent de gestion qui permet de fournir l’ID d’utilisateur externe dans le mappage pour cette application.</span><span class="sxs-lookup"><span data-stu-id="dae5b-121">**Attribute: sourceMA** - Defines the instance name for the source (external) Management Agent that will be used to provide the external UserId in the mapping for this application.</span></span> <span data-ttu-id="dae5b-122">Le nom de l'instance d'agent de gestion externe doit correspondre à un nom d'agent de gestion externe dans MIIS.</span><span class="sxs-lookup"><span data-stu-id="dae5b-122">This external Management Agent instance name must match the name of an external MA instance in MIIS.</span></span>  
  
 <span data-ttu-id="dae5b-123">**Attribut : création de** - en option, valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-123">**Attribute: create** - Optional; default is `true`.</span></span> <span data-ttu-id="dae5b-124">Il indique si des mappages doivent être créés pour cette application.</span><span class="sxs-lookup"><span data-stu-id="dae5b-124">Defines whether mappings should be created for this application.</span></span>  
  
 <span data-ttu-id="dae5b-125">**Attribut : suppression de** - en option, valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-125">**Attribute: delete** - Optional; default is `true`.</span></span> <span data-ttu-id="dae5b-126">Il indique si des mappages doivent être supprimés pour cette application.</span><span class="sxs-lookup"><span data-stu-id="dae5b-126">Defines whether mappings should be deleted for this application.</span></span>  
  
 <span data-ttu-id="dae5b-127">**Élément : SourceMA** : facultatif.</span><span class="sxs-lookup"><span data-stu-id="dae5b-127">**Element: SourceMA** - Optional.</span></span> <span data-ttu-id="dae5b-128">Il identifie les noms du type d'objet et de l'attribut pour une instance d'agent de gestion source (externe) spécifique.</span><span class="sxs-lookup"><span data-stu-id="dae5b-128">Identifies the object type and attribute names for a specific source (external) Management Agent instance.</span></span> <span data-ttu-id="dae5b-129">Si cet élément n'est pas présent pour un agent de gestion spécifique, le type d'objet et les noms des attributs par défaut (respectivement « person » et « uid ») sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="dae5b-129">If this element is not present for a specific Management Agent, then the default object type (“person”) and attribute names (“uid”) are assumed.</span></span> <span data-ttu-id="dae5b-130">Plusieurs éléments `SourceMA` sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="dae5b-130">Multiple `SourceMA` elements are allowed.</span></span>  
  
 <span data-ttu-id="dae5b-131">**Attribut : nom** -le nom de la source (externe) de l’Agent de gestion.</span><span class="sxs-lookup"><span data-stu-id="dae5b-131">**Attribute: name** - The name of the source (external) Management Agent.</span></span> <span data-ttu-id="dae5b-132">Le nom doit correspondre au moins à l'un des noms d'attributs `sourceMA` à partir des éléments `Application`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-132">This name must match at least one of the `sourceMA` attribute names from the `Application` elements.</span></span>  
  
 <span data-ttu-id="dae5b-133">**Attribut : objectType** - en option, valeur par défaut est `person`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-133">**Attribute: objectType** - Optional; default is `person`.</span></span> <span data-ttu-id="dae5b-134">Si le nom du type d'objet qui fournit l'UserId externe ne correspond pas à `person`, vous devez le spécifier ici.</span><span class="sxs-lookup"><span data-stu-id="dae5b-134">If the object type name that provides the external UserId is not `person`, it should be specified here.</span></span>  
  
 <span data-ttu-id="dae5b-135">**Attribut : attribut** - en option, valeur par défaut est `uid`.</span><span class="sxs-lookup"><span data-stu-id="dae5b-135">**Attribute: attribute** - Optional; default is `uid`.</span></span> <span data-ttu-id="dae5b-136">Si le nom de l'attribut qui fournit l'UserId externe ne correspond pas à `uid`, vous pouvez le spécifier ici.</span><span class="sxs-lookup"><span data-stu-id="dae5b-136">If the attribute name that provides the external UserId is not `uid`, you can specify it here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae5b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dae5b-137">See Also</span></span>  
 [<span data-ttu-id="dae5b-138">L’utilisation de l’Agent de gestion ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dae5b-138">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)