---
title: Prise en charge des normes EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2ef14c5-5f12-40e2-93d7-59b5c5a0d641
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb7ab3abb9a4bc547d920614e1a1839a85c593b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="edi-standards-support"></a>Prise en charge des normes
BizTalk Server fournit pour la prise en charge de la conception et exécution de quatre normes de codage. Le tableau suivant répertorie les normes de codage et des liens permettant d'obtenir plus d'informations.  
  
|Norme de codage|Secteur d'activité|Références|  
|-----------------------|----------------------|----------------|  
|UN/EDIFACT|Activité générale|[Site Web de normes](http://go.microsoft.com/fwlink/?LinkId=77532) (référence de la charge utile)<br /><br /> [Règle de codage](http://go.microsoft.com/fwlink/?LinkId=77534) selon ISO 9735-4.1|  
|X12|Activité générale|[Site Web des normes](http://go.microsoft.com/fwlink/?LinkID=28673)<br /><br /> [Développement des spécifications](http://go.microsoft.com/fwlink/?LinkId=77535)|  
|EANCOM|Vente au détail|[Site Web des normes](http://go.microsoft.com/fwlink/?LinkId=92861)|  
|HIPAA X12N|Soins de santé|[Guide de mise en œuvre HIPAA](http://go.microsoft.com/fwlink/?LinkId=77541)<br /><br /> [Spécifications HIPAA](http://go.microsoft.com/fwlink/?LinkId=77542)|  
  
> [!NOTE]
>  Les schémas EANCOM constituent un sous-ensemble d'EDIFACT. EANCOM suit les mêmes règles de codage qu'EDIFACT.  
  
> [!NOTE]
>  KEDIFACT est une norme distincte, mais elle s'inspire de la norme EDIFACT.  
  
## <a name="x12-and-edifact"></a>X12 et EDIFACT  
 Deux normes, ANSI X12 et UN/EDIFACT, représentent plus de 90 % du total des messages EDI échangés globalement.  
  
-   La norme internationale pour les messages EDI UN/EDIFACT (EDIFACT, Échange de données informatisé pour l'administration, le commerce et le transport) a été développée et continue d'être gérée par la Commission économique pour l'Europe des Nations Unies (UN/ECE, United Nations Economic Commission for Europe). Cette norme est également appelée EDIFACT.  
  
-   La norme américaine X12 EDI pour les messages a été développée et continue d'être gérée par le comité Accredited Standards Committee (ASC) X12, organisme accrédité par l'institut ANSI (American National Standards Institute).  
  
 EDIFACT repose en grande partie sur des États-Unis X12 normes. Les deux normes EDI sont très similaires au niveau de la structure. Les différences sont les suivantes :  
  
-   Les éléments structurels sont nommés différemment. Par exemple, l'en-tête de contrôle de l'échange est un élément de données ISA selon la norme X12 et un élément de données UNB selon la norme EDIFACT.  
  
-   Bien que plusieurs documents informatisés renvoient aux deux normes, ceux-ci possèdent un nom différent selon la norme. Par exemple, un bon de commande est un document informatisé 850 selon la norme X12 et un document informatisé ORDERS selon la norme EDIFACT.  
  
-   La norme EDIFACT dispose d'un segment d'en-tête UNA facultatif pour définir des éléments de la structure, tels que les séparateurs/délimiteurs et la notation décimale, qui remplaceront les valeurs par défaut définies dans un pipeline.  
  
-   La norme X12 dispose de deux types d'accusés de réception (un accusé de réception technique appelé TA1 et une notification de transactions opérationnelles appelée 997), tandis que la norme EDIFACT dispose uniquement d'un accusé de réception polyvalent appelé CONTRL.  
  
-   La norme X12 préconise le codage ASCII, tandis que la norme EDIFACT recommande le codage UTF8.  
  
 BizTalk Server prend en charge la norme KEDIFACT (Korea EDIFACT). Elle respecte le Guide de mise en œuvre des messages UN/EDIFACT ; par conséquent, elle s'inspire profondément de la norme EDIFACT. Toutefois, il existe des différences entre les normes KEDIFACT et X12/EDIFACT. KEDIFACT fait appel à plusieurs schémas EDI spécifiques à KEDIFACT et exploite la page de codes KECA.  
  
## <a name="hipaa"></a>HIPAA  
 BizTalk Server prend en charge le traitement de X12, et le traitement HIPAA étant un dérivé de X12 traitement, BizTalk Server prend en charge le traitement HIPAA. Les références à la prise en charge de la norme X12 que vous rencontrerez dans ce document s'appliquent donc également au traitement de la norme HIPAA.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] offre la prise en charge complémentaire spécifique à la norme HIPAA, à savoir :  
  
-   Un ensemble de schémas de document HIPAA de version 4010A1. Pour plus d’informations sur les schémas de document EDI et HIPAA dans BizTalk Server, consultez [des schémas de Document EDI](../core/edi-document-schemas.md).  
  
-   Un ensemble de schémas de document HIPAA de version 5010. Pour plus d’informations, consultez [5010 de Version de schéma de Document HIPAA](../core/hipaa-document-schema-version-5010.md).  
  
-   Le fractionnement d'un sous-document HIPAA. Pour plus d’informations, consultez [fractionnement des sous-documents HIPAA](../core/splitting-hipaa-subdocuments.md).  
  
-   Prise en charge pour les deux premiers niveaux de test WEDI SNIP : X12 intégrité de la syntaxe et les exigences de la [Guide d’implémentation HIPAA](http://go.microsoft.com/fwlink/?LinkId=77541).  
  
 BizTalk Server fournit la prise en charge HIPAA dans le cadre de la fonctionnalité EDI de BizTalk Server native. Pour plus d’informations, consultez [prise en charge EDI dans BizTalk Server](../core/edi-support-in-biztalk-server2.md).  
  
## <a name="eancom"></a>EANCOM  
 BizTalk Server prend en charge le traitement d’EDIFACT, et le traitement EANCOM étant un dérivé de traitement d’EDIFACT, BizTalk Server prend en charge le traitement EANCOM. Les références à la prise en charge de la norme EDIFACT que vous rencontrerez dans ce document s'appliquent donc également au traitement de la norme EANCOM.  
  
 BizTalk Server fournit la prise en charge EANCOM spécifiques supplémentaire :  
  
-   Un ensemble de schémas de document EANCOM de versions EAN94, EAN97 et EAN02. Pour plus d’informations sur les schémas de document EDI et EANCOM dans BizTalk Server, consultez [des schémas de Document EDI](../core/edi-document-schemas.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Structure des messages EDI](../core/edi-message-structure.md)   
 [Schémas de document EDI](../core/edi-document-schemas.md)