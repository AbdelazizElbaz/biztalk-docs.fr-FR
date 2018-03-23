---
title: Comment importer BPEL4WS | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL4WS, restrictions
- BPEL4WS, importing
- BPEL4WS, orchestrations
- orchestrations, BPEL4WS
ms.assetid: 3626fcb9-8e7d-4812-a0c9-bde6e7954ec8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b32a0044321ce6ac57d7bd49c14b40ba17430db
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-import-bpel4ws"></a>Comment importer BPEL4WS
Vous pouvez importer un BPEL4WS existant pour créer une orchestration.  
  
> [!IMPORTANT]
>  Cette version de BizTalk Server est compatible avec BPEL4WS 1.1. Vous ne pouvez pas importer ni exporter BPEL4WS 1.0.  
  
 Pour obtenir un exemple d’importation de BPEL4WS, consultez [BPEL importer (exemple BizTalk Server)](../core/bpel-import-biztalk-server-sample.md).  
  
### <a name="to-import-bpel4ws-into-an-orchestration"></a>Pour importer BPEL4WS dans une orchestration  
  
1.  Créez un projet.  
  
2.  Dans les types de projets BizTalk, double-cliquez sur Projet d'importation BPEL BizTalk Server, ou sélectionnez Projet d'importation BPEL BizTalk Server, puis cliquez sur OK.  
  
3.  Dans l'Assistant, sélectionnez les fichiers BPEL, WSDL et XSD qui doivent être importés pour former le nouveau projet BizTalk. Insérez tous les fichiers référencés avec les instructions importer/inclure.  
  
4.  Sélectionnez les fichiers WSDL pour les services Web appelés.  
  
     Vous pouvez maintenant modifier ou déployer la nouvelle orchestration.  
  
 **Restrictions à l’importation de BPEL4WS**  
  
-   Lorsque vous importez BPEL et WSDL, vérifiez que la propriété Nom du nœud de définition WSDL et le nœud de processus BPEL ne sont pas les mêmes.  
  
-   N'utilisez pas de mots réservés XLANG/s dans le BPEL4WS que vous importez. Pour obtenir la liste complète, consultez [les mots réservés XLANG/s](../core/xlang-s-reserved-words.md).  
  
-   Seuls les types XSD prédéfinis simples sont pris en charge.  
  
-   XSD : QName n’est pas prise en charge ; Il est importé en tant que System.String. Utilisez xsd : String à la place.  
  
-   Pensez à utiliser des XPath canoniques lorsque vous importez BPEL4WS.  
  
     Pour obtenir des performances optimales, il est conseillé de n’importer que des XPath canoniques. Le chemin d'accès complet de la racine au nœud promu doit être développé en utilisant '/* [local-name()="someName" and namespace-uri()="someUri"]'.  
  
     Si vous importez un XPath non canonique, vous pouvez supprimer une promotion et promouvoir à nouveau le même champ pour que l'Éditeur de schémas puisse créer le XPath canonique correct.  
  
     Exemple : (targetNamespace = http://BizTalk_Server_Project3.Schema1)  
  
    ```  
    <element name=Root type=complexType>  
                <sequence>  
                            <element name=promotedField/>  
                </sequence>  
    </element>  
    ```  
  
     XPath - /*[local-name()='Root' and namespace-uri()='http://BizTalk_Server_Project3.Schema1']/\*[local-name()='promotedField' and namespace-uri()='']  
  
    |XPath canonique|XPath non canonique|  
    |---------------------|--------------------------|  
    |L’Éditeur BizTalk affiche une icône spéciale (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) pour indiquer que le champ a été promu. L’utilisation d'expressions XPath canoniques pour la promotion des champs permet d’améliorer les performances grâce à un parcours plus efficace de XML.|L’Éditeur BizTalk n'affiche pas d’icône spéciale. Le compilateur et la boîte de dialogue de promotion émettent des avertissements. Il se produit un effet linéaire mais non trivial sur les performances à mesure que la taille des messages augmente.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment exporter BPEL4WS](../core/how-to-export-bpel4ws.md)   
 [Conversions de types XLANG/s en BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)