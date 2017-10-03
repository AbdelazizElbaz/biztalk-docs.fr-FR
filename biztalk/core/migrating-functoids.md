---
title: Migration des fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, migrating
- migrating, maps
- Migrating functoids, about Migrating functoids
- Migrating functoids
- Scripting functoids
- migrating, functoids
- migrating, Scripting functoids
ms.assetid: fc5b3ac9-28c6-41df-b779-15a8c3188528
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72f9769a571eb9b04cee21e42f5e75afbbadfafa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="migrating-functoids"></a>Migration des fonctoids
Lorsque vous migrez un mappage de versions précédentes de BizTalk Server vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], les fonctoids inclus dans le mappage sont également migrés. Si les fonctoids que vous migrez n’incluent pas **script** fonctoids, aucune tâche de migration supplémentaires n’est nécessaires. Toutefois si votre mappage comprend **script** fonctoids ou des fonctoids personnalisés, vous avez peut-être des étapes supplémentaires à effectuer.  
  
 Dans les versions précédentes de BizTalk Server, tout le script personnalisé inclus dans un **script** fonctoid était écrit inline. Autrement dit, lorsque vous créiez le fonctoid, tout le script appelé par le fonctoid lors de l’exécution était stocké avec le fonctoid. Si vous souhaitez utiliser le même script avec un autre fonctoid, vous soit copié et collé à partir d’un **script** fonctoid à un autre, ou vous réécriviez le script à partir de zéro.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copie les scripts inline existants avec les fonctoids lors de la migration d’un mappage. Toutefois, tous les scripts ne fonctionnent pas correctement. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]utilise Visual Basic .NET et JScript .NET plutôt que du VBScript et JScript utilisés dans les versions précédentes. Les versions .NET des langages incluent des modifications de la syntaxe.  
  
> [!NOTE]
>  Veillez à tester votre **script** fonctoids après la migration.  
  
 Vous devez réécrire les fonctoids personnalisés. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]attend des fonctoids personnalisés à utiliser le .NET framework. Il ne peut pas utiliser les anciens fonctoids personnalisés COM. Les fonctoids personnalisés peuvent être réécrits pour utiliser .NET framework. Pour un exemple de code d’un fonctoid personnalisé, consultez [fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md).  
  
 Une alternative consiste à encapsuler la fonctionnalité du fonctoid personnalisé dans un assembly externe et appeler cet assembly via un **script** fonctoid. La section suivante décrit ce processus.  
  
### <a name="to-migrate-your-custom-functoids"></a>Pour migrer vos fonctoids personnalisés  
  
1.  Recréez la fonctionnalité du fonctoid dans un langage .NET, tel que Microsoft Visual Basic .NET, JScript .NET ou Microsoft Visual C# .NET.  
  
2.  Créez un assembly pour contenir la nouvelle fonctionnalité.  
  
3.  Enregistrez l’assembly dans le Global Assembly Cache (GAC).  
  
    > [!NOTE]
    >  Pour l’enregistrement des assemblys dans le GAC, ils doivent être dotés d'un nom fort et signés. Pour plus d'informations sur l’enregistrement des assemblys, voir « Global Assembly Cache » dans la collection combinée [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
4.  Créer une référence entre le mappage contenant le **script** fonctoid et l’assembly qui contient la fonctionnalité réécrite.  
  
5.  Configurer le **Script** propriété pour le **script** fonctoid. Cette propriété détermine quel script le **script** appelle fonctoid lors de l’exécution. Vous devez faire correspondre la valeur de cette propriété avec le langage dans lequel vous avez converti votre script personnalisé. Pour plus d’informations sur la configuration de la propriété de Script, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md). Consultez également [le fonctoid script](../core/scripting-functoid.md).  
  
6.  Générez le projet BizTalk qui contient le mappage avec le **script** fonctoid.  
  
7.  Validez et testez le mappage.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des propriétés des fonctoids et des paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md)   
 [Fonctoid script](../core/scripting-functoid.md)