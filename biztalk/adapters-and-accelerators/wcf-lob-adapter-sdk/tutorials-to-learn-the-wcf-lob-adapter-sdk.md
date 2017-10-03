---
title: Didacticiels pour apprendre WCF LOB Adapter SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99002b01-da8a-483e-ada3-1ffbe9cd7357
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3efc47a5df445e18e4a78a005c31791fe1f1fa24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorials-to-learn-the-wcf-lob-adapter-sdk"></a>Didacticiels pour apprendre WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] didacticiels contiennent des informations sur la façon dont vous pouvez utiliser [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] pour développer la ligne riche en fonctionnalités des cartes d’entreprise pour faciliter l’intégration d’application d’entreprise au sein de votre entreprise. À l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], les opérations et les données que vous exposez peuvent être consommées par toute application qui peut consommer une liaison WCF, y compris [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 Les didacticiels contiennent des exemples simples construites autour d’un ensemble d’opérations prédéfinies. Vous n’avez pas besoin d’une ligne réelle du système d’entreprise permet d’effectuer ces didacticiels. Toutefois, les détails fournis dans les didacticiels applicable à vos besoins de développement d’adaptateur, à partir des métadonnées de présentation à l’écriture de gestionnaires sortants et au-delà.  

> [!TIP]
> L’adaptateur Echo terminé est inclus dans les fichiers d’installation de BizTalk à `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` ou `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.
  
 Utilisez les didacticiels suivants pour apprendre à utiliser les éléments clés de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
-   [Didacticiel 1 : Développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md). Fournit des instructions détaillées pour la création d’un adaptateur qui expose des opérations de chaînes à partir d’un ensemble de méthodes prédéfinies qui agissent en tant que la ligne du système de l’entreprise. L’adaptateur fournit une implémentation pour la plupart des gestionnaires courantes dans le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] notamment rechercher, Parcourir, opérations entrantes et sortantes. Au terme de ce didacticiel, vous aurez une carte fonctionnelle.  
  
-   [Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md). Fournit des instructions détaillées pour la consommation de l’adaptateur d’écho développés dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) à partir d’un projet .NET. Vous ajoutez une référence de service d’adaptateur à un nouveau projet et fournir du code pour tester les opérations entrantes et sortantes de l’adaptateur de l’écho.  
  
-   [Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md). Fournit des instructions détaillées de hébergeant l’adaptateur Echo développés dans [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) traiter de dans les Services (IIS). Vous utiliserez également svcutil.exe (Service Model Metadata) pour créer une application client simple pour consommer l’opération EchoString de l’adaptateur hébergé.  
  
 Ces didacticiels fournissent une approche structurée pour comprendre certaines des fonctionnalités clés de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Ils peuvent être remplis avec aucune connaissance de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] ou [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. Toutefois, vous en apprendrez davantage si vous comprenez les concepts de conception de la carte et comprenez comment la conception de l’adaptateur est facilitée par la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. Pour plus d'informations, consultez :  
  
-   [Tâches courantes de développeur pour WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/common-developer-tasks-for-the-wcf-lob-adapter-sdk.md)  
  
-   [Les composants clés de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/key-components-of-the-wcf-lob-adapter-sdk.md)  
  
 Avant de commencer ces didacticiels, vous devez passer en revue la configuration requise dans [avant de commencer les didacticiels](../../core/before-you-begin-the-tutorial.md).  
  
 
## <a name="in-this-section"></a>Dans cette section  
  
-   [Avant de commencer les didacticiels](../../core/before-you-begin-the-tutorial.md)  
  
-   [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)  
  
-   [Didacticiel 2 : Utiliser l’adaptateur d’écho à partir de .NET](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-2-consume-the-echo-adapter-from-net.md)  
  
-   [Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de BizTalk Server](../../core/getting-started-with-biztalk-server.md)