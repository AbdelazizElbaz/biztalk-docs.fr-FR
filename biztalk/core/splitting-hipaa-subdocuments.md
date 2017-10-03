---
title: Fractionnement de sous-documents HIPAA | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66d9badd-00c6-43a3-807e-0ad313983adc
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 799cb5813b3c13339a0c477bf142a467a91b2c94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-hipaa-subdocuments"></a>Fractionnement de sous-documents HIPAA
Les échanges EDI pour HIPAA ont généralement plusieurs documents enfants ou sous-documents dans un document informatisé unique, liés par les en-têtes ST/SE. Le pipeline de réception EDI prend en charge la création de sous-documents HIPAA distincts d'un tel document informatisé. Cela diffère des échanges EDI non HIPAA dans lesquels un document informatisé unique est traité comme un message unique.  
  
## <a name="subdocument-splitting-schemas"></a>Schémas de fractionnement en sous-documents  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge le fractionnement des types de documents HIPAA suivants par le biais de schémas natifs :  
  
-   Documents de version 4010 HIPAA : 834 Enrollment, 835 Claim Payment et trois variantes de 837 Claim  
  
-   Documents de la version 5010 HIPAA : 276/277 Claim Status – demande et réponse, 834 Enrollment et trois variantes de 837 Claim  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit deux versions de schémas pour chacun de ces trois types de documents. Pour chaque type de document, le schéma prenant en charge le fractionnement est identifié par la balise « Multiple » dans le nom de fichier. L'autre schéma ne prend pas en charge le fractionnement en sous-documents.  
  
 Dans certains scénarios, les schémas de fractionnement et de non-fractionnement peuvent être nécessaires. Cela est pris en charge par l'utilisation d'un espace de noms cible personnalisé pour une variante du schéma.  
  
## <a name="how-subdocument-splitting-is-enabled"></a>Activation du fractionnement en sous-documents  
 Le fractionnement en sous-documents HIPAA est activé par trois entrées d'annotation dans le schéma HIPAA. Les deux premières sont des entrées pour le schéma dans l’annotation appinfo, qui doit être définie sur **Oui**:  
  
```  
subdocument_break = "yes" Split_Without_Sibling_Data = "Yes"  
```  
  
 La troisième entrée d'annotation se trouve aux niveaux d'enregistrement appropriés au sein du schéma HIPAA. Cette propriété doit également être définie sur **Oui**.  
  
```  
subdocument_creation_break = "yes"  
```  
  
 Un échange HIPAA est fractionné en sous-documents uniquement si l'annotation Séparateur de création de sous-document au sein du schéma HIPAA est définie sur « yes » et que la propriété du tiers de l'option de traitement par lot entrant est définie sur « Fractionner l'échange sous forme de documents informatisés ». Si la propriété du tiers de l'option de traitement par lot entrant est définie pour conserver l'échange, le Désassembleur EDI ne fractionne pas l'échange en sous-documents. Dans ce cas, le Désassembleur EDI ignore l'annotation. Aucun avertissement n'est déclenché dans l'observateur d'événements si cela se produit.  
  
> [!NOTE]
>  Les annotations Séparateur de création de sous-document ne peuvent pas être imbriquées. Si un schéma inclut une boucle avec une annotation de sous-document appliquée, cette boucle ne peut pas contenir une autre boucle avec une annotation de sous-document appliquée.  
  
## <a name="how-subdocuments-are-processed"></a>Traitement des sous-documents  
 Le Désassembleur EDI dans le pipeline de réception EDI fractionne les sous-documents. Une fois que le pipeline de réception valide l'échange entrant et génère les accusés de réception appropriés, il achemine chaque sous-document distinct à la MessageBox. Chaque sous-document est valide en termes de structure et de syntaxe. Cependant, on s'attend à ce que les récapitulatifs au niveau de l'entreprise, les totaux de documents informatisés et les numéros de contrôle de document informatisé soient hors de la synchronisation. Le pipeline d'envoi remplace la valeur du numéro de segment existant dans SE01 de chaque sous-document (provenant du document informatisé d'origine) par le nombre de segments inclus dans le sous-document. Le pipeline de réception rétablit également les numéros de contrôle de document informatisé dans chaque sous-document, de sorte que ce dernier n'ait pas de numéros de contrôle en double. Cela garantit la réussite du traitement côté envoi.  
  
 Si un document informatisé échoue la validation EDI ou étendue lors du fractionnement en sous-documents, le document informatisé individuel défaillant est interrompu.  
  
 Un port d'envoi qui s'abonne aux sous-documents récupère chaque sous-document de la MessageBox, sérialise les sous-documents XML, les traite par lot (si activé), les valide et les envoie. Le pipeline d'envoi met à jour le nombre de segments Élément de données (SE01).  
  
## <a name="how-subdocuments-are-split"></a>Fractionnement en sous-documents  
 Une annotation Séparateur de création de sous-document est généralement appliquée à une boucle qui englobe un ou plusieurs éléments au sein d'un schéma HIPAA. D'autres éléments avant et après la boucle du séparateur dans le schéma sont répliqués dans chaque sous-document.  
  
 Le tableau suivant illustre un exemple de fractionnement en sous-documents. Dans cet exemple, l'annotation Séparateur de création de sous-document est définie sur « yes » pour la boucle de l'élément CC. Par conséquent, les éléments CC du document informatisé sont séparés en sous-documents distincts, tandis que les éléments AA, BB et DD du document informatisé sont tous inclus dans chaque sous-document distinct.  
  
|Schéma (nombre minimal/maximal d'occurrences)|Instance d'origine|Sous-document n° 1|Sous-document #2|Sous-document #3|  
|---------------------------------------|-----------------------|---------------------|---------------------|---------------------|  
|ST (1,0)|ST|ST|ST|ST|  
|AA (1,1)|AA|AA|AA|AA|  
|Boucle BB (1,n)<br /><br /> BB1 (1,n)<br /><br /> Boucle CC (1,n) - subdocument_break = "yes"<br /><br /> CC1 (1,n)<br /><br /> CC2 (0,n)<br /><br /> BB2 (0,n)|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1<br /><br /> BB1\*2<br /><br /> CC1\*2<br /><br /> CC2\*2<br /><br /> BB1\*3<br /><br /> CC1\*3<br /><br /> CC2\*3|BB1*1<br /><br /> CC1\*1<br /><br /> CC2\*1<br /><br /> BB2\*1|BB1*2<br /><br /> CC1\*2<br /><br /> CC2\*2|BB1*3<br /><br /> CC1\*3<br /><br /> CC2\*3|  
|DD (0,n)|DD|DD|DD|DD|  
|SE|SE|SE|SE|SE|