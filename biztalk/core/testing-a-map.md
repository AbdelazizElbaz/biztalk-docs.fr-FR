---
title: "Test d’un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265afd62-3c1d-4b9a-9f51-176b9b079241
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee4c59783dd72e94ee222c0ee165c7c8f90a32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-a-map"></a>Test d’un mappage
Vous pouvez tester un mappage dans un projet au moment de la conception. Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Cette rubrique explique comment configurer et utiliser le **Test Map** fonctionnalité de l’extension de l’outil XML.  
  
 Pour tester un mappage, spécifiez un document source et le dossier dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera une instance générée (avec des données fictives). Vous devez définir les délimiteurs que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour traiter le document source et générer le document de destination en fonction des schémas EDI. Cela est vrai pour toutes les valeurs de la **TestMap** d’entrée de propriété dans les pages de propriétés de la carte : **générer l’Instance**, **XML**, ou **natif**. Ceci est vrai pour **générer l’Instance** car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a besoin de connaître les délimiteurs à utiliser pour générer l’instance. Ceci est vrai pour **XML** ou **natif** car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a besoin de savoir comment interpréter le fichier plat natif ou le fichier XML. Vous devez également définir les délimiteurs que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera lors de la génération du fichier de sortie.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-test-a-map"></a>Pour tester un mappage  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ajoutez le mappage que vous souhaitez tester à un projet, puis ajoutez les schémas source et de destination de ce mappage au projet.  
  
    > [!NOTE]
    >  Il n'est pas nécessaire de créer le projet pour tester le mappage.  
  
2.  Avec le bouton droit de la carte, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés** , configurez **valider l’entrée TestMap** à **True** si vous souhaitez valider le fichier d’entrée par rapport au schéma source. Définissez **valider la sortie TestMap** à **True** si vous souhaitez valider le fichier de sortie par rapport au schéma de destination.  
  
    > [!NOTE]
    >  Si vous testez un mappage avec le **entrée TestMap** propriété la valeur **natif** et **valider l’entrée TestMap** et **valider la sortie TestMap** les propriétés définies sur **False**, la validation est toujours effectuée. Cela est dû au fait que le fichier d'entrée natif est converti au format XML et que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide le code XML par rapport au schéma. S’il existe des problèmes de validation dans l’instance d’entrée, le mécanisme de validation génère des erreurs, même si le **valider l’entrée TestMap** et **valider la sortie TestMap** propriétés sont définies sur **False**.  
  
4.  Définissez **entrée TestMap** à **natif** pour un fichier d’entrée qui a une extension EDI ou. Affectez-lui la valeur **XML** s’il a une extension .xml. Définissez **entrée TestMap** à **générer l’Instance** avoir [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] générer une instance d’entrée, au lieu de désigner une instance d’entrée manuellement.  
  
5.  Définissez **sortie TestMap** à **natif** pour un fichier de sortie qui a une extension EDI ou. Affectez-lui la valeur **XML** s’il a une extension .xml.  
  
6.  Pour **Instance d’entrée TestMap**, accédez à l’instance d’entrée que vous souhaitez utiliser pour tester le mappage, sélectionnez-le, puis **ouvrir**. Si vous souhaitez laisser cette propriété vide, la valeur **entrée TestMap** à **générer l’Instance**.  
  
    > [!NOTE]
    >  Vous devez soit désigner une instance d’entrée pour **Instance d’entrée TestMap** ou **entrée TestMap** à **générer l’Instance**. Dans le cas contraire, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère une erreur.  
  
7.  Pour **Instance de sortie TestMap**, accédez à l’emplacement que vous souhaitez enregistrer l’instance de sortie, entrez un nom pour l’instance de sortie, puis cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Si vous ne désignez aucune instance de sortie, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée un fichier de sortie, le place dans un dossier, puis indique les noms du fichier et du chemin d'accès.  
  
8.  Avec le bouton droit de la carte que vous testez, puis cliquez sur **Test Map**.  
  
9. Dans le X12 **propriétés de l’Instance EDI** boîte de dialogue, vérifiez que toutes les propriétés sont cohérentes avec les paramètres pour les instances d’entrée et de sortie.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Affiche la **propriétés de l’Instance EDI** boîte de dialogue à deux reprises au cours du processus TestMap : une fois pour l’interprétation de l’instance de message d’entrée et une fois pour la génération de l’instance de message de sortie. Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut afficher la boîte de dialogue plus de deux fois, ainsi qu'afficher celle-ci pour les schémas non-EDI. Dans ce cas, cliquez sur **OK** pour fermer la boîte de dialogue.  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’outils au moment du Design XML](../core/using-design-time-xml-tools.md)