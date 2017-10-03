---
title: "Exécution de tests unitaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40275d0b-b2ee-400c-9ef5-b9386ab0ae53
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b594aa02cbecb21a20180d1143f2f8835788a958
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performing-unit-testing"></a>Exécution de tests unitaires
Test unitaire se concentre au niveau du composant et est essentiellement un test de réussite/échec qui vérifie si des composants individuels de la solution BizTalk fonctionnent comme prévu. Vous avez plusieurs options pour votre solution BizTalk de tests unitaires.  
  
## <a name="using-visual-studio"></a>Utilisation de Visual Studio  
 Les fonctionnalités de test unitaire sont disponible avec Visual Studio 2008 et versions ultérieures. Pour plus d’informations sur la fonctionnalité de test qui est disponible dans Visual Studio, consultez [test de l’Application](http://go.microsoft.com/fwlink/?LinkId=159595) (http://go.microsoft.com/fwlink/?LinkId=159595).  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]fournit également un fonctionnalité de test unitaire pour permettre aux utilisateurs de créer des tests unitaires pour les schémas, mappages et pipelines. Pour plus d’informations sur cette fonctionnalité, consultez [tests unitaires avec les projets BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=158270) (http://go.microsoft.com/fwlink/?LinkId=158270).  
  
> [!NOTE]  
>  Visual Studio est très utile pour les artefacts de BizTalk, tels que des orchestrations, schémas, pipelines et les composants de pipeline de tests unitaires. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Fournit des classes de test que vous pouvez utiliser avec Visual Studio Team System pour tester des artefacts BizTalk.  
  
## <a name="using-non-microsoft-tools"></a>À l’aide des outils Non - Microsoft  
 Deux autres outils utilisés pour les solutions BizTalk de tests unitaires sont **BizUnit** et **NUnit**. **BizUnit** fonctionne de façon transparente avec Visual Studio Team System Test Edition. De même, **NUnit** tests peuvent être modifiés facilement afin qu’ils peuvent s’exécuter en tant que-est dans Visual Studio Team System Test Edition. Pour plus d’informations sur ces outils, consultez [outils de test](~/technical-guides/tools-for-testing.md).  
  
> [!NOTE]  
>  Utilisation de **BizUnit** et **NUnit** ne sont pas pris en charge par Microsoft, et Microsoft n’apporte aucune garantie quant à l’adéquation de ces programmes. L'utilisation de ces programmes relève de votre seule responsabilité.  
  
## <a name="using-the-biztalk-server-sdk"></a>À l’aide du Kit de développement logiciel de BizTalk Server  
 Vous pouvez effectuer unité tester d’autres artefacts de BizTalk avec les utilitaires disponibles dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Kit de développement logiciel. Le tableau ci-dessous fournit un résumé des utilitaires dans le Kit de développement logiciel qui peut être utilisé pour les tests unitaires :  
  
|**Utilitaire**|**Fonction**|  
|-----------------|-----------------|  
|Utilitaire Expéditeur AS2|Vous permet d’envoyer un message AS2 vers un site Web sur un seul ordinateur. Il simule l'envoi d'un message AS2 à partir d'un ordinateur distinct.|  
|DSDump.exe|Vous permet de vider la structure des schémas de document (représentation simplifiée en mémoire du ou des schémas XSD) avec ou sans annotations de fichier plat. Cet outil pourra vous être utile si le moteur d'analyse vous envoie des erreurs comme $Root$0$3$2 et que vous devez les décoder. Les chiffres suivants $ représentent les index ou les enregistrements de base 0 tels qu'ils apparaissent dans le schéma de document.|  
|FFAsm.exe|Exécute le composant Assembleur de fichier plat, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise ou assemble le ou les documents XML d'un utilisateur en un document de fichier plat.|  
|FFDasm.exe|Exécute le composant Désassembleur de fichier plat, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse ou désassemble le document de fichier plat d'un utilisateur en un ou plusieurs documents XML.|  
|Pipeline.exe|Exécute un envoi ou réception de pipeline ; accepte un ou plusieurs documents d’entrée et leurs parties, les schémas XSD et les informations connexes ; et s’exécute un document de sortie après le pipeline de produit. Pipeline.exe n’a pas accès [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données, c’est le cas pipelines contenant des composants assembleur et Désassembleur BizTalk Framework qui accèdent aux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données lors de l’exécution ne peuvent pas pris en charge.|  
|XMLAsm.exe|Exécute le composant Assembleur XML, l'appelle directement en émulant un pipeline d'envoi, le but étant que vous puissiez voir comment il sérialise, assemble ou enveloppe le ou les documents XML d'un utilisateur en un document XML de sortie.|  
|XMLDasm.exe|Exécute le composant Désassembleur XML, l'appelle directement en émulant un pipeline de réception, le but étant que vous puissiez voir comment il analyse, désassemble ou désenveloppe le document XML d'un utilisateur en un ou plusieurs documents XML.|  
  
 Pour plus d’informations sur les utilitaires disponibles dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK, consultez [utilitaires dans le Kit de développement logiciel](http://go.microsoft.com/fwlink/?LinkId=154387) (http://go.microsoft.com/fwlink/?LinkId=154387).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de test](~/technical-guides/tools-for-testing.md)