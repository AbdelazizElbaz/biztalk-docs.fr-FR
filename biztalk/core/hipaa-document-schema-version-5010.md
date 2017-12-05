---
title: "Version de schéma 5010 de Document HIPAA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62e50964-66e1-4ed9-a1a1-68556b13b024
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e464fc26e5a98edd8ee99dad159d5faa068998aa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="hipaa-document-schema-version-5010"></a>Version de schéma de document HIPAA 5010
La valeur par défaut Department of Health and Human Services (HHS) a annoncé une règle finale 16 janvier 2009, qui remplace la version actuelle HIPAA 4010 a 1 avec la version 5010. Version 5010 des normes HIPAA inclut des améliorations dans structurelle, liminaires, technique et le contenu des données. Ces améliorations réduira et éliminer les ambiguïtés dans les données lors de l’adressage également quelques besoins précédemment non remplie. BizTalk Server prend en charge la version 5010.  
  
> [!NOTE]
>  BizTalk Server continue à prendre en charge la version HIPAA 4010 a 1.  
  
## <a name="hipaa-5010-version-support"></a>Prise en charge de la version HIPAA 5010  
 Les modifications suivantes ont été introduites dans le cadre de la prise en charge de la loi HIPAA 5010 par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   **Nouveaux schémas de remplacement**: version HIPAA 5010 introduit de nouveaux schémas de remplacement suivants sur la version antérieure 4010 a 1. Les schémas EDI sont compressés et inclus dans l'exécutable ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe). Une fois exécuté, MicrosoftEdiXSDTemplates.exe place les schémas HIPAA 5010 dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\HIPAA\5010.  
  
    |GS08/ST03|ID de document informatisé (ST01)| Description|  
    |----------------|----------------------|-----------------|  
    |005010X279|270|Eligibility, Coverage or Benefit Inquiry - Request|  
    |005010X279|271|Eligibility, Coverage or Benefit Information - Response|  
    |005010X212|276|Health Care Claim Status - Request|  
    |005010X212|277|Health Care Claim Status - Response|  
    |005010X217|278|Health Care Services Review – Request and Response|  
    |005010X218|820|Payroll Deduction|  
    |005010X220|834|Health Care Benefit(s) Enrollment and Maintenance|  
    |005010X221|835|Health Care Claim Payment(s)|  
    |005010X222|837|Health Care Claim(s) - Professional|  
    |005010X223A1|837|Health Care Claim(s) - Institutional|  
    |005010X224A1|837|Health Care Claim(s) - Dental|  
  
-   **Prise en charge pour le champ ST03**: Version 5010 exige la présence de ST03 dans toutes les transactions définit autres que 835 (Payment(s)) de revendication de soins de santé. ST03 permet d'identifier la version du document informatisé. ST03 autorise différentes versions des documents informatisés au sein d'un groupe unique. ST03 est prioritaire sur GS08 dans l'identification de la version du document informatisé. Vous pouvez écrire et promouvoir ST03 sous l'espace de noms du schéma de propriété EDI comme propriété de contexte et acheminer les messages sur la base de ST03.  
  
-   **Prise en charge des documents informatisés similaires au sein d’un groupe**: X12 normes fournissent un mappage entre les documents informatisés et groupes, connus comme le mappage ST01-GS01. Ceci permet de valider des documents informatisés similaires qui peuvent être combinés au sein d'un groupe (GS-GE). Dans le cadre de la loi HIPAA, ceci implique qu'une demande 837 (Professional, Institutional et Dental) peut maintenant survenir au sein d'un seul groupe.  
  
-   **Prise en charge de ICD-10**: ensembles de code de transaction électronique sont utilisés pour la transmission des données de santé. La version 5010 prend en charge l'utilisation des jeux de code ICD-10 (International Classification of Diseases), incompatibles avec la version 4010A1. ICD-10 permet d'identifier divers diagnostics et procédures dans le cadre de la facturation des demandes de remboursement, des transactions associées et de la génération de rapports cliniques. L'utilisation d'ICD-10 accroît la précision des informations relatives aux services des patients, aux diagnostics et aux traitements et améliore la qualité des données incluses dans les rapports.  
  
-   **Nouveaux champs dans les 997 5010**: le 997 accusé de réception fonctionnel schéma fourni out-of-the-box par BizTalk Server introduit trois nouveaux champs facultatifs à savoir AK103, AK203 et AK41.3. Le moteur EDI est capable de traiter un 5010 entrant message 997 qui contient ces champs, mais ne génèrent pas d’accusé de réception 997 sortant en fonction du nouveau schéma.  
  
 Il y avait un problème connu avec les schémas HIPAA 4010A1 dans lequel les longueurs minimale et maximale des éléments du type de données X12_R n'étaient pas vérifiées. Dans BizTalk Server ce problème a été résolu et les schémas HIPAA 5010 valident des éléments du type de données X12_R pour les longueurs minimales et maximale.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge HIPAA dans BizTalk Server](../core/hipaa-support-in-biztalk-server.md)   
 [Fractionnement de sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md)