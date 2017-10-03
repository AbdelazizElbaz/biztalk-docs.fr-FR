---
title: "Scripts utilisant Inline XSLT et modèles d’appel XSLT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3168417-3653-4c9e-a09c-184ffdc0ccb2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7c4c1d8eff582d15f9ce022053b80f2dea2f856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scripting-using-inline-xslt-and-xslt-call-templates"></a><span data-ttu-id="8db53-102">Scripts utilisant Inline XSLT et les modèles d’appels Inline XSLT</span><span class="sxs-lookup"><span data-stu-id="8db53-102">Scripting Using Inline XSLT and XSLT Call Templates</span></span>
<span data-ttu-id="8db53-103">Vous pouvez directement écrire des feuilles de style XSLT Extensible Stylesheet Language Transformations () pour une utilisation dans les **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="8db53-103">You can directly write Extensible Stylesheet Language Transformations (XSLT) stylesheets for use in the **Scripting** functoid.</span></span> <span data-ttu-id="8db53-104">Cela vous permet de procéder à des transformations que les liens et les fonctoids intégrés risquent de ne pas pouvoir représenter.</span><span class="sxs-lookup"><span data-stu-id="8db53-104">This enables you to perform transformations, that links and built-in functoids may not be able to represent.</span></span> <span data-ttu-id="8db53-105">Il existe deux types de scripts XSLT : inline modèles d’appel XSLT et XSLT.</span><span class="sxs-lookup"><span data-stu-id="8db53-105">There are two kinds of XSLT scripts: inline XSLT and XSLT call templates.</span></span> <span data-ttu-id="8db53-106">Lorsque vous effectuez une sélectionnez dans le **sélectionner le type de script** liste déroulante dans le **configurer le fonctoid script** boîte de dialogue, l’exemple de code apparaît que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="8db53-106">When you select either in the **Select script type** dropdown in the **Configure Scripting Functoid** dialog box, sample code appears that you may use.</span></span>  
  
 <span data-ttu-id="8db53-107">Les scripts inline XSLT et les modèles d’appel inline XSLT peuvent appeler des fonctions d’assemblys externes.</span><span class="sxs-lookup"><span data-stu-id="8db53-107">Inline XSLT scripts and inline XSLT call templates may call functions in external assemblies.</span></span> <span data-ttu-id="8db53-108">Ces appels exige la définition du **XML avec extensions personnalisées** propriété de la grille.</span><span class="sxs-lookup"><span data-stu-id="8db53-108">Making such calls requires setting the **Custom Extension XML** property of the grid.</span></span> <span data-ttu-id="8db53-109">Pour plus d’informations, consultez **XML avec extensions personnalisées (propriété de grille)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="8db53-109">For more information, see **Custom Extension XML (Grid Property)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="inline-xslt"></a><span data-ttu-id="8db53-110">Inline XSLT</span><span class="sxs-lookup"><span data-stu-id="8db53-110">Inline XSLT</span></span>  
 <span data-ttu-id="8db53-111">Un script inline XSLT ne peut produire que des sorties.</span><span class="sxs-lookup"><span data-stu-id="8db53-111">An inline XSLT script may only produce output.</span></span> <span data-ttu-id="8db53-112">Le **script** fonctoid ne peut pas avoir tous les liens d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8db53-112">The **Scripting** functoid may not have any input links.</span></span> <span data-ttu-id="8db53-113">Il doit également établir un lien direct à un enregistrement ou à un champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="8db53-113">The functoid must also directly link to a record or field in the destination schema.</span></span>  
  
 <span data-ttu-id="8db53-114">En outre, le script est chargé de la création du nœud cible et des structures sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="8db53-114">In addition, the script is responsible for creating the target node and any structures underneath it.</span></span>  
  
 <span data-ttu-id="8db53-115">Le message d’instance d’entrée suivant comporte deux éléments représentant des informations de contact.</span><span class="sxs-lookup"><span data-stu-id="8db53-115">The following input instance message contains two elements representing contact information.</span></span>  
  
```  
<ns0:SourceInstance xmlns:ns0="http://SourceInstanceNamespace">  
    <Address>  
        <Contact>Karin Zimprich</Contact>  
        <ContactType>Referral</ContactType>  
    </Address>  
</ns0:SourceInstance>  
```  
  
 <span data-ttu-id="8db53-116">Le script inline XSLT suivant, entré dans le tampon de script, convertit le **Contact** et **ContactType** champs aux attributs.</span><span class="sxs-lookup"><span data-stu-id="8db53-116">The following inline XSLT script, entered in the script buffer, converts the **Contact** and **ContactType** fields to attributes.</span></span>  
  
```  
<ContactInfo xmlns:p="http://SourceInstanceNamespace">  
     <xsl:variable name="var:var1" select="/p:SourceInstance/Address/ContactType" />  
     <xsl:attribute name="ContactType">  
          <xsl:value-of select="$var:var1" />  
     </xsl:attribute>  
     <xsl:variable name="var:var2" select="/p:SourceInstance/Address/Contact" />  
     <xsl:attribute name="Contact">  
          <xsl:value-of select="$var:var2" />  
     </xsl:attribute>  
</ContactInfo>  
```  
  
 <span data-ttu-id="8db53-117">Le script produit la sortie suivante, dans l’hypothèse d’un schéma de sortie approprié, lorsqu’il est exécuté par rapport au message d’instance d’entrée précédent.</span><span class="sxs-lookup"><span data-stu-id="8db53-117">The script produces the following output, assuming an appropriate output schema, when run against the preceding input instance message.</span></span>  
  
```  
<ns0:OutInstance xmlns:ns0="http://More_XSLT.Out">  
    <ContactInfo ContactType="Referral" Contact="Karin Zimprich" xmlns:p="http://SourceInstanceNamespace">  
    </ContactInfo>  
</ns0:OutInstance>  
```  
  
 <span data-ttu-id="8db53-118">Notez que l’absence de liens vers les **script** fonctoid n’empêche pas le script XSLT à partir de l’obtention de données à partir du message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8db53-118">Notice that the absence of links to the **Scripting** functoid does not prevent the XSLT script from getting data from the input instance message.</span></span> <span data-ttu-id="8db53-119">Le script spécifie les chemins d’accès aux valeurs d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8db53-119">The script specifies paths to the input instance values.</span></span>  
  
 <span data-ttu-id="8db53-120">Pour un autre exemple d’un script inline XSLT, voir [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).</span><span class="sxs-lookup"><span data-stu-id="8db53-120">For another example of an inline XSLT script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="inline-xslt-call-templates"></a><span data-ttu-id="8db53-121">Modèles d'appel Inline XSLT</span><span class="sxs-lookup"><span data-stu-id="8db53-121">Inline XSLT Call Templates</span></span>  
 <span data-ttu-id="8db53-122">Tout comme un script inline XSLT, un modèle d’appel inline XSLT doit directement se connecter à un nœud de destination.</span><span class="sxs-lookup"><span data-stu-id="8db53-122">Like an inline XSLT script, an inline XSLT call template must connect directly to a destination node.</span></span> <span data-ttu-id="8db53-123">Cependant, il peut utiliser des liens à partir du schéma source et d’autres fonctoids.</span><span class="sxs-lookup"><span data-stu-id="8db53-123">However, an inline XSLT call template may use links from the source schema and from other functoids.</span></span>  
  
 <span data-ttu-id="8db53-124">Le modèle d’appel est chargé de la création du nœud de destination et de ses sous-structures.</span><span class="sxs-lookup"><span data-stu-id="8db53-124">The call template is responsible for creating the destination node and any of its substructures.</span></span>  
  
 <span data-ttu-id="8db53-125">Exemple de modèle d’appel XSLT concaténant deux éléments apparaît dans le **d’entrée de script** de la mémoire tampon lorsque vous sélectionnez **modèle d’appel XSLT Inline** dans les **sélectionner le type de script** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="8db53-125">A sample XSLT call template that concatenates two elements appears in the **Input script** buffer when you select **Inline XSLT Call Template** in the **Select script type** dropdown.</span></span>  
  
 <span data-ttu-id="8db53-126">Pour un autre exemple d’un modèle d’appel inline XSLT, voir [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).</span><span class="sxs-lookup"><span data-stu-id="8db53-126">For another example of an inline XSLT call template, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db53-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8db53-127">See Also</span></span>  
 <span data-ttu-id="8db53-128">[Fonctoid script](../core/scripting-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="8db53-128">[Scripting Functoid](../core/scripting-functoid.md) </span></span>  
 <span data-ttu-id="8db53-129">[Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="8db53-129">[Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md) </span></span>  
 <span data-ttu-id="8db53-130">[Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span><span class="sxs-lookup"><span data-stu-id="8db53-130">[Scripting Using Inline C#, JScript .NET, and Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md) </span></span>  
 <span data-ttu-id="8db53-131">[Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="8db53-131">[How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="8db53-132">Comment configurer le fonctoid script</span><span class="sxs-lookup"><span data-stu-id="8db53-132">How to Configure the Scripting Functoid</span></span>](../core/how-to-configure-the-scripting-functoid.md)