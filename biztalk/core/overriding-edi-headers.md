---
title: "Remplacement des en-têtes EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c19d3d-eab2-4d44-8752-25aeadb537a4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 510a3817d0fd99d43b6da9462c74dd8bc7c1bdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overriding-edi-headers"></a>Remplacement des en-têtes EDI
Lors de l'envoi d'un message codé EDI, l'enveloppe EDI appliquée au message est généralement basée sur les propriétés EDI de l'accord récepteur ou sur celles de l'accord de secours. Cependant, il est souvent utile de définir les propriétés de l'enveloppe EDI en fonction de valeurs générées par le composant d'exécution.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez utiliser les propriétés de contexte EdiOverride pour préciser les valeurs utilisées pour générer l'enveloppe EDI sur les documents sortants.  
  
## <a name="using-edioverride-context-properties"></a>Utilisation des propriétés de contexte EdiOverride  
 Les propriétés de contexte EdiOverride offrent un moyen de remplacer tout ou partie des valeurs utilisées pour générer l'enveloppe EDI. Le pipeline d'envoi EDI utilise les propriétés de contexte EdiOverride contenant une valeur valide pour construire l'enveloppe. Si une propriété n'est pas renseignée, le pipeline utilise la valeur spécifiée dans les propriétés de l'accord, ou dans les propriétés de l'accord de secours si aucun accord n'est défini. Si une propriété contient une valeur non valide, le pipeline interrompt le message et signale une erreur de validation.  
  
> [!NOTE]
>  Les valeurs spécifiées dans la collection EdiOverride ne sont utilisées que si la propriété `EdiOverride.OverrideEdiHeader` est écrite dans le contexte d'un message et contient une valeur True.  
>   
>  La valeur par défaut n'est pas définie.  
  
### <a name="edioverride-properties-for-x12-envelope-values"></a>Propriétés EdiOverride pour les valeurs d'une enveloppe X12  
 Le tableau suivant répertorie les propriétés de contexte EdiOverride et l'en-tête d'enveloppe X12 correspondant :  
  
|En-tête|Propriétés|  
|------------|----------------|  
|En-tête de contrôle de l'échange (ISA)|ISA01, ISA02, ISA03, ISA04, ISA05, ISA06, ISA07, ISA08, ISA09, ISA10, ISA11, ISA12, ISA13, ISA14, ISA15, ISA16|  
|En-têtes de groupe fonctionnel (GS)|GS01, GS02, GS03, GS04, GS05, GS06, GS07, GS08|  
|En-tête du document informatisé|ST02|  
  
### <a name="edioverride-properties-for-edifact-envelope-values"></a>Propriétés EdiOverride pour les valeurs d'une enveloppe EDIFACT  
 Le tableau suivant répertorie les propriétés de contexte EdiOverride et le segment d'enveloppe EDIFACT correspondant :  
  
|Segment|Propriétés|  
|-------------|----------------|  
|Options de l'échange (UNA)|UNA1, UNA2, UNA3, UNA4, UNA5, UNA6, UNA6Suffix|  
|En-tête de contrôle de l'échange (UNB)|UNB1_1, UNB1_2, UNB2_1, UNB2_2, UNB2_3, UNB3_1, UNB3_2, UNB3_3, UNB4_1, UNB4_2, UNB5, UNB6_1, UNB7, UNB8, UNB9, UNB10, UNB11|  
|En-têtes de groupe fonctionnel (UNG)|UNG1, UNG2_1, UNG2_2, UNG3_1, UNG3_2, UNG4_1, UNG4_2, UNG5, UNG6, UNG7_1, UNG7_2, UNG7_3, UNG8|  
|En-tête du message (UNH)|UNH1|  
  
 Les segments EDIFACT UNA et UNG étant facultatifs, les propriétés GenerateUNA et GenerateUNG peuvent être utilisées pour déterminer si ces en-têtes sont générés, indépendamment de la **appliquer le segment UNA** paramètre d’accord. Les tableaux suivants indiquent les valeurs provoquant la génération de ces segments :  
  
|Propriété de conxte GenerateUNA|Paramètre d'accord Appliquer le segment UNA|Comportement du moteur|  
|----------------------------------|-----------------------------------------|---------------------|  
|TRUE|CHECKED|Générer UNA|  
|TRUE|UNCHECKED|Générer UNA|  
|FALSE|CHECKED|Ne pas générer un UNA|  
|FALSE|UNCHECKED|Ne pas générer un UNA|  
|Absent (OverrideEDIHeader est faux)|CHECKED|Générer UNA|  
|Absent (OverrideEDIHeader est faux)|UNCHECKED|Ne pas générer un UNA|  
  
|Propriété de conxte GenerateUNG|Paramètre d'accord Appliquer les segments UNG|Comportement du moteur|  
|----------------------------------|------------------------------------------|---------------------|  
|TRUE|CHECKED|Générer UNG|  
|TRUE|UNCHECKED|Générer UNG|  
|FALSE|CHECKED|Ne pas générer un UNG|  
|FALSE|UNCHECKED|Ne pas générer un UNG|  
|Absent (OverrideEDIHeader est faux)|CHECKED|Générer UNG|  
|Absent (OverrideEDIHeader est faux)|UNCHECKED|Ne pas générer un UNG|  
  
### <a name="group-envelopes"></a>Enveloppes de groupe  
 Les enveloppes de groupe sont particulièrement délicates à utiliser car l'échange peut avoir plusieurs groupes. Pour surmonter cette difficulté, le pipeline d'envoi EDI peut appliquer l'enveloppe à tous les groupes de l'échange ou au seul groupe de l'échange.  
  
 Pour les transactions uniques, tous les champs GS ou UNG peuvent être remplacés alors que pour les échanges par lot, seuls les champs suivants peuvent être remplacés :  
  
-   GS04  
  
-   GS05  
  
-   UNG4_1  
  
-   UNG4_2  
  
### <a name="batching"></a>Traitement par lot  
 L'orchestration du traitement par lot gère le remplacement du numéro de contrôle du document informatisé des messages traités par lot. Les propriétés suivantes peuvent être écrites dans le contexte de tout message qui sera traité par lot pour remplacer le numéro de contrôle du document informatisé :  
  
-   ST02 (pour les messages X12)  
  
-   UNH1 (pour les messages EDIFACT)  
  
> [!NOTE]
>  Si plusieurs messages entrants contiennent le même numéro de contrôle dans le même groupe, les messages dont les numéros sont dupliqués sont suspendus.  
  
> [!NOTE]
>  Ne faites pas la promotion des propriétés de contexte EdiOverride ISA, UNA, GS ou UNG pour les messages qui ne sont pas traités par lot. Si vous devez remplacer ces propriétés, faites-en la promotion sur le message de sortie de l'orchestration de traitement par lot avant l'envoi au pipeline d'envoi EDI.  
  
### <a name="delimiter-collision"></a>Collision entre délimiteurs  
 Les délimiteurs, comme les en-têtes UNA, doivent contenir une valeur unique pour chaque champ. Lorsque vous remplacez des valeurs de délimiteurs, comme les en-têtes UNA, vous devez vous assurer que chaque valeur de délimiteur est unique, non seulement au sein des valeurs que vous remplacez mais également parmi les valeurs de délimiteur utilisées à partir des paramètres de l'accord ou des paramètres de l'accord de secours.  
  
 Si, par exemple, vous remplacez UNA1, UNA2 et UNA4 et UNA3, UNA5, UNA6 et UNA6Suffix provenant des propriétés de l'accord, chaque propriété doit contenir une valeur unique par rapport aux autres.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)