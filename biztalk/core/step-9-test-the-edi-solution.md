---
title: "Étape 9 : Tester la Solution EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7a44e0f-496c-462f-bf03-1c2f842d13b6
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6e308ae230ea2d78ff03ed02a81310c38fbcabc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-test-the-edi-solution"></a>Étape 9 : Tester la Solution EDI
![Étape 9 de 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 Dans le cadre de cette rubrique, vous allez tester votre traitement entrant et afficher le rapport d'état EDI-Interchange pour les informations relatives au traitement.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="testing-the-solution"></a>Test de la solution  
  
1.  Dans l'Explorateur Windows, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations. Copie le **SamplePO.txt** fichier.  
  
2.  Coller le **SamplePO.txt** de fichiers dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM dossier.  
  
3.  Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem. Vérifiez que le dossier contient un fichier txt de sortie.  
  
4.  Ouvrez le fichier de sortie figurant dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem et le fichier d'entrée SamplePO.txt figurant dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations. Vérifiez que les données dans le message de sortie correspondant aux données d’origine **SamplePO.txt** fichier.  
  
    > [!NOTE]
    >  Vous pouvez vérifier que les données figurant dans le fichier de sortie ont été transformées à partir des données figurant dans le fichier d'entrée en ouvrant le fichier Inbound4010850_to_OrderFile.btm dans Visual Studio, puis en contrôlant les mappages.  
  
5.  Accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Développer Tutorial\ProcessEDI_TestLocations\Scenario A\toTHEM_997. Vérifiez que le dossier contient un fichier txt d'accusé de réception 997 de sortie dans lequel l'élément de données ST01 est « 997 ».  
  
6.  Dans l’arborescence de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **groupe BizTalk**. Au bas du volet droit, cliquez sur **échange EDI et état ACK corrélé**.  
  
7.  Dans l’expression de requête, modifiez l’opérateur le **état** au champ **est égal à** et modifiez le **valeur** champ pour le **état** au champ **Tous les**. Supprimer le **champ échange Date heure** (sélectionnez la ligne et appuyez sur Supprimer dans le tableau de clés).  
  
8.  Cliquez sur **exécuter la requête**.  
  
9. Vérifiez que deux messages s'affichent dans le rapport d'état, l'un dans le sens réception de THEM (Fabrikam) vers US (OrderSystem) (le message 850), l'autre dans le sens envoi de US (OrderSystem) à THEM (Fabrikam) (accusé de réception 997).  
  
10. Double-cliquez sur le message de THEM à US. Dans le **état et les détails de l’accusé de réception de l’échange** boîte de dialogue, vérifiez que les détails de l’échange sont affichés dans le volet droit.  
  
11. Cliquez sur **ACK(s) fonctionnel**. Vérifiez que les détails du rapport de l'accusé de réception sont affichés dans le volet droit.  
  
12. Fermez boîte de dialogue État de l'échange et détails de l'accusé de réception.  
  
13. Dans le **état échange/ACK** volet, cliquez sur le message de THEM à US, puis cliquez sur **détails du document informatisé**. Cliquez sur l’entrée dans le **résultats de la requête** volet, puis cliquez sur **vue de contenu du document informatisé**. Vérifiez que les données du document informatisé sont affichées dans le **détails du Message** boîte de dialogue. Dans l'Explorateur Windows, ouvrez le fichier SamplePO.txt dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] SDK\ProcessEDI_TestLocations. Vérifiez que le document informatisé affiché dans le **détails du Message** boîte de dialogue est identique à celui dans le message d’entrée, sans les en-têtes d’échange et de groupe et les codes de fin.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez terminé le didacticiel pour développeur d'interface EDI.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : EDI Interface Developer Tutorial.](../core/tutorial-2-edi-interface-developer-tutorial.md)   
 [Étape 1 : Préparer le didacticiel pour développeur d’Interface EDI](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)