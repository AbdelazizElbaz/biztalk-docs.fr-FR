---
title: Utiliser des espaces de noms avec le Proxy WSDL dans WCF LOB Adapter SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 781d20fa-83e3-42fa-866e-5650d5eb71a7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc85d47da81d2d7425c7db4aad90ea32389f7d84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk"></a>Utiliser des espaces de noms avec le Proxy WSDL dans WCF LOB Adapter SDK
Le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] génère WSDL et des proxys pour un adaptateur à l’aide des valeurs fournies par le développeur à l’aide de la [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] ou spécifié dans le code par une modification de la variable privée SERVICENAMESPACE et/ou `Namespace` propriété de l’adaptateur.  
  
 Les types de schéma et les éléments définis dans le \<WSDL : types >\<schéma > utilisent le {OperationNamespace} par défaut. Si un type particulier a un TypeNamespace substituée définie dans le **TypeMetadata** de l’objet, cet espace de noms est utilisé pour le type complexe et/ou ou définition de l’élément.  
  
## <a name="impact-on-wsdl"></a>Impact sur WSDL  
 Le tableau suivant montre comment les différents espaces de noms dans un adaptateur personnalisé affectent le WSDL correspondant. Dans la table, ~ {OperationNamespace} est le mappage d’espace de noms de classe d’un URI ; par exemple, si {OperationNamespace} est « myscheme://a.b/c », ~ {OperationNamespace} sera myscheme.a.b.c.  
  
|Construction WSDL|Syntaxe|  
|--------------------|------------|  
|TargetNamespace WSDL,<br /><br /> Xmlns:TS|{Personnalisé} Adapter.Namespace|  
|\<WSDL : portType >|{schéma de}. ~ {OperationNamespace}|  
|Nom du Message d’entrée WSDL|{schéma de}. ~ {OperationNamespace} _ {NomOpération} _InputMessage|  
|Nom de Message de sortie WSDL|{schéma de}. ~ {OperationNamespace} _ {NomOpération} _OutputMessage|  
|\<WSDL : types >\<schéma > targetNamespace|{schéma}  :// {OperationNamespace}|  
|\<élément >\<complexType >|Utilisez {TypeNamespace} si sa valeur n’est pas null ou vide.|  
  
## <a name="impact-on-proxy"></a>Impact sur le serveur Proxy  
 Trois attributs différents dans le proxy sont affectées par les espaces de noms :  
  
-   [**System.ServiceModel.ServiceContractAttribute**(nom = « {schéma}. ~ {OperationNamespace} », Namespace="{Custom}Adapter.Namespace »]  
  
-   [**System.ServiceModel.MessageContractAttribute**(attributs WrapperName = « DivideResponse », WrapperNamespace = « {schéma}  :// {OperationNamespace} », IsWrapped = true)]  
  
-   [**System.ServiceModel.MessageBodyMemberAttribute**(Namespace = « {schéma}  :// {TypeNamespace} », ordre = 0)]  
  
## <a name="see-also"></a>Voir aussi  
 [Recommandées de développement à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)