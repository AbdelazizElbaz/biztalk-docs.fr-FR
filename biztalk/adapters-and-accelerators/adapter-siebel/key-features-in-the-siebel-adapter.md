---
title: "Les fonctionnalités de l’adaptateur Siebel clés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- features, performance-related
- adapter features, new
- features, technology-related
- features, metadata-related
- adapter features, operations-related
- adapter features, performance-related
- features, new
- features, operations-related
- adapter features, metadata-related
ms.assetid: 4612c9ab-810e-4c69-9168-a25c58682e71
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 295ff8b13358109a5d4737fb5f9325b3c9caa0f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="key-features-in-the-siebel-adapter"></a>Fonctionnalités clés de l’adaptateur Siebel
Cette section répertorie les nouvelles fonctionnalités dans [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
> [!NOTE]
>  Cette rubrique a été utilisée à partir de la version précédente de [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] aide.  
  
## <a name="new-features-in-the-siebel-adapter"></a>Nouvelles fonctionnalités de l’adaptateur Siebel  
 Voici les nouvelles fonctionnalités introduites dans cette version de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
### <a name="technology-related-features"></a>Fonctionnalités liées à la technologie  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge pour l’utilisation de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec Microsoft Office SharePoint Server (MOSS)|Vous pouvez utiliser les adaptateurs de présenter des données à partir du système Siebel sur un portail MOSS. Pour plus d’informations, consultez [à l’aide de l’adaptateur Siebel avec Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx).|  
  
### <a name="operations-related-features"></a>Liées aux opérations de fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Prise en charge pour l’opération d’association sur des composants d’entreprise|Les clients de l’adaptateur peuvent associer des enregistrements en spécifiant les expressions de recherche pour le parent et enfant. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples (multiples). Notez que les expressions de recherche doivent filtrer un seul enregistrement de composants d’entreprise à la fois parent et enfant.|  
|Prise en charge pour dissocier une opération sur les composants d’entreprise|Les clients de l’adaptateur peuvent dissocier les enregistrements en spécifiant les expressions de recherche pour le parent et enfant. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples (multiples). Notez que les expressions de recherche doivent filtrer un seul enregistrement de composants d’entreprise à la fois parent et enfant.|  
|Prise en charge des requêtes de lien à valeurs multiples|Les clients de l’adaptateur peuvent interroger les enregistrements enfants associés à un enregistrement parent en spécifiant l’enregistrement parent et le nom du champ à valeurs multiples. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples (multiples).|  
  
### <a name="other-features"></a>Autres fonctionnalités  
  
|Fonctionnalité|Commentaire|  
|-------------|-------------|  
|Nouvelle façon d’utiliser l’adaptateur dans[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]|Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-Siebel dans BizTalk. Si vous souhaitez utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut. Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] via un port WCF-Siebel, vous devez d’abord ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour plus d’informations, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)