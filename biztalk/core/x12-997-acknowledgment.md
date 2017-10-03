---
title: "X12 accusé de réception 997 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a352fb-635c-4f0e-9844-4b250159333d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1868c6c644940c49f854282980efc09c631b2cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="x12-997-acknowledgment"></a>Accusé de réception 997 X12
L'accusé de réception fonctionnel 997 X12 indique l'état d'un échange reçu. Il signale chaque erreur rencontrée lors du traitement du document reçu. Le pipeline de réception EDI BizTalk génère toujours un 997 compatible 4010. Toutefois, le pipeline de réception EDI et les pipelines d'envoi EDI peuvent également valider un 997 compatible 5010.  
  
 Comme tous les documents informatisés X12, l'accusé de réception 997 est envoyé à l'intérieur d'une enveloppe GS/GE. Les ST et SE ne diffèrent pas d'un autre document informatisé.  
  
 Les segments dans le document informatisé d'un accusé de réception 997 sont répertoriés dans le tableau suivant.  
  
|Position|Segment<br />ID|Nom|Demande<br />Des.|Nombre Utiliser|Boucle<br />Répétez l’opération|  
|--------------|-----------------|----------|----------------|--------------|------------------|  
|010|ST|En-tête de document informatisé (pour l'accusé de réception)|M|1|-|  
|020|AK1|En-tête de réponse du groupe fonctionnel|M|1|-|  
|030|AK2|En-tête de réponse du document informatisé|O|1|999999 <br />(ID boucle = AK2)|  
|040|AK3|Note de segment de données|O|1|999999 <br />(ID boucle = AK2/AK3)|  
|050|AK4|Note d'élément de données|O|99|-|  
|060|AK5|Code de fin de réponse du document informatisé|M|1|-|  
|070|AK9|Code de fin de réponse du groupe fonctionnel|M|1|-|  
|080|SE|Code de fin du document informatisé (pour l'accusé de réception)|M|1|-|  
  
-   Demande Des. = Désignation de l’exigence  
  
-   O = obligatoire  
  
-   F = facultatif  
  
 Les segments AK sont décrits ci-après. Les segments dans la boucle AK2 à AK5 fournissent des informations sur une erreur avec un document informatisé.  
  
## <a name="ak1"></a>AK1  
 Le segment AK1 obligatoire identifie le groupe fonctionnel faisant l'objet d'un accusé de réception avec les éléments de données suivants :  
  
-   AK101 est l'ID de groupe fonctionnel (GS01) du groupe fonctionnel faisant l'objet d'un accusé de réception.  
  
-   AK102 est le numéro de contrôle de groupe (GS06 et GE02) du groupe fonctionnel faisant l'objet d'un accusé de réception.  
  
-   AK103 est facultatif et est la version d'implémentation EDI envoyée dans le GS08 de la transaction d'origine. AK103 prend en charge le 997 entrant compatible 5010.  
  
## <a name="ak2"></a>AK2  
 Le segment AK2 facultatif contient un accusé de réception pour un document informatisé dans le groupe fonctionnel reçu. S'il existe plusieurs segments AK2, ils sont envoyés sous la forme d'une série de boucles. Chaque boucle AK2 identifie un document informatisé dans l'ordre de sa réception. Le segment AK2 identifie le document informatisé avec deux éléments de données :  
  
-   AK201 est l'ID de document informatisé (ST01) du document informatisé faisant l'objet d'un accusé de réception.  
  
-   AK202 est le numéro de contrôle de document informatisé (ST02 et SE02) du document informatisé faisant l'objet d'un accusé de réception.  
  
-   AK203 est facultatif et est la version d'implémentation EDI envoyée dans le ST03 de la transaction d'origine. AK203 prend en charge le 997 entrant compatible 5010.  
  
 Une boucle AK2 contient les segments AK3, AK4 et AK5 si un document informatisé est erroné. Pour plus d'informations, consultez les descriptions de ces segments ci-après.  
  
 Vous pouvez spécifier que les segments AK2 sont générés pour tous les documents informatisés, acceptés ou rejetés, ou uniquement pour les documents informatisés rejetés. BizTalk Server génère les segments AK2 pour les documents informatisés acceptés (où AK501 == A) si vous sélectionnez le **inclure une boucle AK2 pour les documents informatisés acceptés** case à cocher dans la **accusés de réception** page de la Boîte de dialogue Propriétés de contrat pour un accord entre deux profils d’entreprise (ou le **accusés de réception** page de la X12 onglet Paramètres pour un profil d’entreprise). Sinon, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère des boucles AK2 uniquement pour les documents informatisés rejetés. Si un accord n'est pas résolu pour l'échange faisant l'objet d'une réponse, les paramètres de génération de l'accusé de réception 997 sont par défaut les paramètres d'accord de secours, et les segments AK2 ne sont pas générés pour les documents informatisés acceptés.  
  
## <a name="ak3"></a>AK3  
 Le segment AK3 facultatif signale des erreurs dans un segment de données et identifie l'emplacement du segment de données. Un segment AK3 est créé pour chaque segment d'un document informatisé comportant une ou plusieurs erreurs. S'il existe plusieurs segments AK3, ils sont envoyés sous la forme d'une série de boucles (un segment par boucle). Le segment AK3 a quatre éléments de données qui spécifient l'emplacement de chaque segment erroné et indique le type d'erreur syntaxique trouvée à cet emplacement :  
  
-   AK301 identifie le segment erroné avec son ID de segment X12, par exemple NM1.  
  
-   AK302 est le numéro de segment du segment erroné. Le segment ST a la valeur « 1 » et chaque segment incrémente le numéro de segment d'un.  
  
-   AK303 identifie une boucle liée : une boucle entourée d’un segment LS et un segment LE. AK303 contient les valeurs des segments LS et LE qui lient le segment erroné.  
  
-   AK304 est le code d'erreur de l'erreur dans le segment de données. AK304 est facultatif, mais il est obligatoire s'il existe une erreur pour le segment identifié. Pour obtenir la liste des codes d’erreur AK304, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
## <a name="ak4"></a>AK4  
 Le segment AK4 facultatif signale des erreurs dans un élément de données ou une structure de données composites et identifie l'emplacement de l'élément de données. Il est envoyé lorsque l'élément de données AK304 a la valeur « 8 », « Un segment comporte des erreurs d'élément de données ». Il peut répéter jusqu'à 99 fois au sein de chaque segment AK3. Le segment AK4 a quatre éléments de données qui spécifient l'emplacement de chaque élément de données ou structure de données composites erroné et indique le type d'erreur syntaxique trouvée à cet emplacement :  
  
-   AK401 est un élément de données composites avec des champs AK41.1, AK41.2 et AK41.3. AK401-1 identifie l'élément de données ou la structure de données composites erroné avec son numéro. Par exemple, si le second élément de données dans le segment a une erreur, AK401 a la valeur « 2 ». AK401-2 identifie le numéro de l'élément de données composites dans une structure de données composites qui comporte une erreur. Lorsque AK401 signale une erreur dans une structure de données non composites, AK401-2 n'a pas de valeur.  
  
     AK41.3 est facultatif et est la position de l'élément de données répétées. AK41.3 prend en charge le 997 entrant compatible 5010.  
  
-   AK402 est facultatif et identifie le simple numéro d'élément de données X12 de l'élément erroné. Par exemple, NM101 est le simple numéro d'élément de données X12 98.  
  
-   AK403 est obligatoire et signale l'erreur de l'élément identifié. Pour obtenir la liste des codes d’erreur AK403, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
-   AK404 est facultatif et contient une copie de l'élément de données identifié erroné. AK404 n'est pas utilisé si l'erreur indique un caractère non valide.  
  
## <a name="ak5"></a>AK5  
 Le segment AK5 indique si le document informatisé identifié dans le segment AK2 est accepté ou rejeté et pourquoi. Le segment AK5 est obligatoire si la boucle AK2 facultative est incluse dans l'accusé de réception. Le segment AK4 a un élément de données obligatoire qui spécifie l'état du document informatisé et un à cinq éléments de données facultatifs qui fournissent des codes d'erreur en fonction de la syntaxe du document informatisé.  
  
-   AK501 spécifie si le document informatisé identifié est accepté ou rejeté. Pour obtenir la liste des codes d’erreur AK501, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
-   AK502 à AK506 indiquent la nature de l'erreur. Pour obtenir la liste des codes d’erreur AK501, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
## <a name="ak9"></a>AK9  
 Le segment AK9 obligatoire indique si le groupe fonctionnel identifié dans le segment AK1 est accepté ou rejeté et pourquoi. Le segment AK9 a quatre éléments de données obligatoires qui spécifient l'état du document informatisé et la nature de l'erreur, ainsi qu'un à cinq éléments de données facultatifs qui spécifient les erreurs relevées.  
  
-   AK901 est obligatoire et spécifie si le groupe fonctionnel identifié dans AK1 est accepté ou rejeté. Pour obtenir la liste des codes d’erreur AK901, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
-   AK902 spécifie le nombre de documents informatisés inclus dans le code de fin du groupe fonctionnel identifié (GE01).  
  
-   AK903 spécifie le nombre de documents informatisés reçus.  
  
-   AK904 spécifie le nombre de documents informatisés acceptés dans le groupe fonctionnel identifié.  
  
-   AK905 à AK909 peuvent indiquer une à cinq erreurs relevées dans le groupe fonctionnel identifié. Pour obtenir la liste de AK905 à AK909 des codes d’erreur, consultez [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [X12 des Codes d’erreur d’accusé de réception 997](../core/x12-997-acknowledgment-error-codes.md)