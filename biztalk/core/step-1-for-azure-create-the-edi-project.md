---
title: "Étape 1 (pour Azure) : Créer le projet EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d353129-04f0-456b-b371-b346959f5155
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51264a79480031bd334dfb7d699a3a701f2c0254
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-1-for-azure-create-the-edi-project"></a>Étape 1 (pour Azure) : Créer le projet EDI
Dans cette section, Contoso utilise la version de l’[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] d’avril 2012 pour créer un projet EDI. Dans le cadre du projet, Contoso ajoute les éléments suivants :  
  
-   Un schéma de commande client interne (**ECommerceSalesOrder.xsd**) à laquelle le X12 sera transformé le schéma de commande client EDI 840. Contoso utilise le schéma interne pour traiter le message après sa réception dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   Une transformation (**EDI840TOSALESORDER. TRFM**) pour convertir le X12 840 ventes schéma à la **ECommerceSalesOrder** schéma.  
  
 Contoso utilise ces artefacts lors de la création d’un accord dans le portail Azure BizTalk dans l’[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].  
  
### <a name="to-create-edi-project"></a>Pour créer un projet EDI  
  
1.  Ouvrez Visual Studio, à partir de la **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **Service Bus**. Spécifiez un nom de projet et un emplacement pour le projet, puis cliquez sur **OK**.  
  
##  <a name="BKMK_CreateSchema"></a>Pour créer un schéma dans le projet EDI  
  
1.  À partir de l’Explorateur de solutions, cliquez sur le nom de projet que vous venez de créer, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **schéma**, spécifiez le nom du schéma en tant que **ECommerceSalesOrder.xsd**, puis cliquez sur **ajouter**.  
  
3.  Modifiez et construisez le schéma pour qu’il ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-16"?>  
    <xs:schema xmlns="http://ECommerceSalesOrder.Inbound" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://ECommerceSalesOrder.Inbound" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="SalesOrder">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="CompanyCode" type="xs:string" />  
            <xs:element name="PartID" type="xs:int" />  
            <xs:element name="Quantity" type="xs:int" />  
            <xs:element name="AskPrice" type="xs:decimal" />  
            <xs:element name="RequestShipmentDate" type="xs:date" />  
            <xs:element name="Address">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Line1" type="xs:string" />  
                  <xs:element name="Line2" type="xs:string" />  
                  <xs:element name="City" type="xs:string" />  
                  <xs:element name="State" type="xs:string" />  
                  <xs:element name="Country" type="xs:string" />  
                  <xs:element name="Zipcode" type="xs:int" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Contact">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="Firstname" type="xs:string" />  
                  <xs:element name="Lastname" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
            <xs:element name="Comments" type="xs:string" />  
            <xs:element name="DateNow" type="xs:date" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
     Vous pouvez utiliser l’Éditeur de schéma pour construire ce schéma. Pour plus d’informations, consultez [à l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md).  
  
4.  Enregistrez le schéma.  
  
##  <a name="BKMK_CreateTrfm"></a>Pour créer une transformation dans le projet EDI  
  
1.  À partir de l’Explorateur de solutions, cliquez sur le nom de projet que vous venez de créer, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **modèles installés**, sélectionnez **carte**, spécifiez le nom du schéma en tant que **Edi840ToSalesOrder.trfm**, puis cliquez sur **ajouter**.  
  
3.  Dans le mappage, pour le schéma source, sélectionnez **X12_00401_840.xsd**. Il s’agit du schéma X12 standard pour une commande client EDI. Ce schéma doit être déjà ajouté au projet EDI que vous avez créé. Vous pouvez télécharger cette et autres X12 schémas à partir de [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057). Le X12 schémas font partie de la **MicrosoftEdiXSDTemplates.zip** package disponible à partir de l’emplacement de téléchargement.  
  
4.  Pour le schéma de destination, sélectionnez **ECommerceSalesOrder.xsd**. Vous avez créé ce schéma auparavant dans cette rubrique.  
  
5.  Créez le mappage en connectant les nœuds pertinents dans les schémas source et cible.  
  
6.  Enregistrez le mappage.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)