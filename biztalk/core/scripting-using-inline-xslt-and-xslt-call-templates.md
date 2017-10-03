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
# <a name="scripting-using-inline-xslt-and-xslt-call-templates"></a>Scripts utilisant Inline XSLT et les modèles d’appels Inline XSLT
Vous pouvez directement écrire des feuilles de style XSLT Extensible Stylesheet Language Transformations () pour une utilisation dans les **script** fonctoid. Cela vous permet de procéder à des transformations que les liens et les fonctoids intégrés risquent de ne pas pouvoir représenter. Il existe deux types de scripts XSLT : inline modèles d’appel XSLT et XSLT. Lorsque vous effectuez une sélectionnez dans le **sélectionner le type de script** liste déroulante dans le **configurer le fonctoid script** boîte de dialogue, l’exemple de code apparaît que vous pouvez utiliser.  
  
 Les scripts inline XSLT et les modèles d’appel inline XSLT peuvent appeler des fonctions d’assemblys externes. Ces appels exige la définition du **XML avec extensions personnalisées** propriété de la grille. Pour plus d’informations, consultez **XML avec extensions personnalisées (propriété de grille)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="inline-xslt"></a>Inline XSLT  
 Un script inline XSLT ne peut produire que des sorties. Le **script** fonctoid ne peut pas avoir tous les liens d’entrée. Il doit également établir un lien direct à un enregistrement ou à un champ du schéma de destination.  
  
 En outre, le script est chargé de la création du nœud cible et des structures sous-jacentes.  
  
 Le message d’instance d’entrée suivant comporte deux éléments représentant des informations de contact.  
  
```  
<ns0:SourceInstance xmlns:ns0="http://SourceInstanceNamespace">  
    <Address>  
        <Contact>Karin Zimprich</Contact>  
        <ContactType>Referral</ContactType>  
    </Address>  
</ns0:SourceInstance>  
```  
  
 Le script inline XSLT suivant, entré dans le tampon de script, convertit le **Contact** et **ContactType** champs aux attributs.  
  
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
  
 Le script produit la sortie suivante, dans l’hypothèse d’un schéma de sortie approprié, lorsqu’il est exécuté par rapport au message d’instance d’entrée précédent.  
  
```  
<ns0:OutInstance xmlns:ns0="http://More_XSLT.Out">  
    <ContactInfo ContactType="Referral" Contact="Karin Zimprich" xmlns:p="http://SourceInstanceNamespace">  
    </ContactInfo>  
</ns0:OutInstance>  
```  
  
 Notez que l’absence de liens vers les **script** fonctoid n’empêche pas le script XSLT à partir de l’obtention de données à partir du message d’instance d’entrée. Le script spécifie les chemins d’accès aux valeurs d’instance d’entrée.  
  
 Pour un autre exemple d’un script inline XSLT, voir [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## <a name="inline-xslt-call-templates"></a>Modèles d'appel Inline XSLT  
 Tout comme un script inline XSLT, un modèle d’appel inline XSLT doit directement se connecter à un nœud de destination. Cependant, il peut utiliser des liens à partir du schéma source et d’autres fonctoids.  
  
 Le modèle d’appel est chargé de la création du nœud de destination et de ses sous-structures.  
  
 Exemple de modèle d’appel XSLT concaténant deux éléments apparaît dans le **d’entrée de script** de la mémoire tampon lorsque vous sélectionnez **modèle d’appel XSLT Inline** dans les **sélectionner le type de script** liste déroulante.  
  
 Pour un autre exemple d’un modèle d’appel inline XSLT, voir [XML outils (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid script](../core/scripting-functoid.md)   
 [Écriture de scripts à l’aide des assemblys externes](../core/scripting-using-external-assemblies.md)   
 [Scripts utilisant Inline c#, JScript .NET et Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [Comment ajouter des fonctoids de script à une carte](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [Comment configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md)