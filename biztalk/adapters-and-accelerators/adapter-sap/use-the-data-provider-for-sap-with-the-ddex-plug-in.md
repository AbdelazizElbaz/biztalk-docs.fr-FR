---
title: Utiliser le fournisseur de données pour SAP avec le plug-in DDEX | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DDEX plug-in
- DDEX plug-in, Data Provider for SAP
- Data Provider for SAP, using with DDEX plug-in
ms.assetid: b16c8634-172a-4630-87ed-2073a75afdec
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2a1dd348b6d897e147d6add49499e9716a67aeb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="use-the-data-provider-for-sap-with-the-ddex-plug-in"></a>Utiliser le fournisseur de données pour SAP avec le plug-in DDEX
Si vous avez choisi d’installer le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] avec la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] l’installation, le programme d’installation installe un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] plug-in DDEX. Vous pouvez utiliser ce plug-in pour rechercher des objets SAP à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Cette section fournit des informations sur l’utilisation du plug-in DDEX.  
  
 Vous pouvez utiliser le plug-in pour établir la connexion avec le système SAP, ajouter des tables à partir du système SAP et ajouter des modules de fonction à partir du système SAP. Après avoir ajouté les tables et les modules de fonction à l’aide de plug-in Visual Studio, les tables récemment ajoutées et les modules de fonction sont répercutées dans le fichier SAPDiscoveredObjects.xml. Pour plus d’informations sur ce fichier, consultez [sur le fichier SAPDiscoveredObjects.xml dans SAP](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md).  
  
## <a name="prerequisites"></a>Configuration requise  
 Assurez-vous que vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation.  
  
### <a name="to-connect-to-an-sap-system-using-the-ddex-plug-in"></a>Pour vous connecter à un système SAP à l’aide du plug-in DDEX  
  
1.  Démarrez Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **vue** menu, cliquez sur **l’Explorateur de serveurs**.  
  
3.  Dans le **l’Explorateur de serveurs**, avec le bouton droit **des connexions de données**, puis sélectionnez **ajouter une connexion**.  
  
4.  Dans le **modifier la Source de données** boîte de dialogue, à partir de la **source de données** boîte, sélectionnez  **\<autres\>**.  
  
5.  À partir de la **fournisseur de données** la liste déroulante, sélectionnez **fournisseur de données .NET Framework pour mySAP Business Suite** et cliquez sur **OK**. Le **ajouter une connexion** boîte de dialogue s’ouvre.  
  
6.  Le **ajouter une connexion** boîte de dialogue répertorie les paramètres de connexion pour se connecter à un système SAP. Une chaîne de connexion par défaut pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert :  
  
    -   Les paramètres de connexion pour un type de connexion. Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] prend en charge les types de connexion A, B et D. Pour vous connecter à un système SAP, vous devez fournir les paramètres de connexion pour les *un* de ces types de connexion. Par exemple, pour le type de connexion A, vous devez fournir le nom de l’hôte d’application serveur et le numéro du système.  
  
    -   Les informations de connexion pour se connecter à un système SAP, telles que le nom d’utilisateur et mot de passe.  
  
     Pour plus d’informations sur la chaîne de connexion pour se connecter à un système SAP à l’aide du [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
     Dans le **ajouter une connexion** boîte de dialogue, spécifiez :  
  
    -   Les paramètres de connexion pour n’importe quel type d’une seule connexion.  
  
    -   Les informations de connexion pour se connecter à un système SAP.  
  
    -   Si vous voulez activer le débogage de l’interface utilisateur graphique SAP.  
  
    -   Si vous souhaitez utiliser le suivi du Kit de développement logiciel RFC.  
  
     Cliquez sur **OK**. Un nouveau nœud de connexion est créé sous le **des connexions de données** nœud portant le nom de serveur que vous avez spécifié à l’étape précédente.  
  
7.  Développez le nouveau nœud de connexion pour afficher les **Tables** et **fonction Modules** nœuds.  
  
     L’illustration suivante montre l’Explorateur de serveurs une fois que la connexion est établie.  
  
     ![Les plug DDEX&#45;dans pour le fournisseur SAP ADO.NET](../../adapters-and-accelerators/adapter-sap/media/158afc11-9c90-4333-bc62-5901f8d0c794.gif "158afc11-9c90-4333-bc62-5901f8d0c794")  
  
### <a name="to-add-tables-from-an-sap-system-using-the-ddex-plug-in"></a>Pour ajouter des tables à partir d’un système SAP à l’aide du plug-in DDEX  
  
1.  Dans le **l’Explorateur de serveurs**, avec le bouton droit le **Tables** nœud et cliquez sur **rechercher et ajouter des Tables**.  
  
2.  Dans le **nom de table de recherche** texte, spécifiez une chaîne de recherche pour rechercher des tables dans le système SAP, puis cliquez sur **recherche**.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend en charge uniquement le caractère astérisque (*) pour la recherche de tables.  
  
3.  Le **résultats de la recherche** zone répertorie les noms de table qui satisfont les critères de recherche.  
  
     ![Les plug DDEX&#45;dans la boîte de dialogue nom rechercher et ajouter des Tables](../../adapters-and-accelerators/adapter-sap/media/737fc9c3-5258-4693-a2f3-5b5b8d2483e9.gif "737fc9c3-5258-4693-a2f3-5b5b8d2483e9")  
  
4.  Activez la case à cocher correspondant aux tables que vous souhaitez ajouter, cliquez sur **ajouter**. Pour sélectionner toutes les tables, cliquez sur **sélectionner tout**. Pour effacer toutes les sélections, cliquez sur **Effacer tout**.  
  
5.  Une boîte de dialogue vous informe que les tables ajoutées serait visibles après avoir actualisé la **Tables** nœud. Cliquez sur **OK**.  
  
6.  Cliquez sur le **Tables** nœud et sélectionnez **Actualiser**. Les tables sélectionnées apparaissent sous le **Tables** nœud. Cliquez sur un nom de table pour afficher les propriétés de la table dans le **propriétés** volet.  
  
7.  Développez un nom de table pour afficher les champs de la table. Cliquez sur un nom de champ pour afficher les propriétés de champ dans le **propriétés** volet.  
  
### <a name="to-add-rfcs-from-an-sap-system-using-the-ddex-plug-in"></a>Pour ajouter les RFC à partir d’un système SAP à l’aide du plug-in DDEX  
  
1.  Dans le **l’Explorateur de serveurs**, avec le bouton droit le **fonction Modules** nœud et cliquez sur **rechercher et ajouter des Modules de fonction**.  
  
2.  Dans le **module de fonction de recherche** texte, spécifiez une chaîne de recherche pour rechercher des modules de la fonction dans le système SAP, puis cliquez sur **recherche**.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend en charge uniquement le caractère astérisque (*) pour la recherche des modules fonctionnelles.  
  
3.  Le **résultats de la recherche** zone répertorie les modules de fonction qui répondent aux critères de recherche.  
  
     ![Les plug DDEX&#45;dans la boîte de dialogue Rechercher et ajouter des Modules](../../adapters-and-accelerators/adapter-sap/media/8c7f9081-80aa-4bfe-8f06-2c751758ddd0.gif "8c7f9081-80aa-4bfe-8f06-2c751758ddd0")  
  
4.  Sélectionnez la case à cocher correspondant aux modules (fonction) que vous souhaitez ajouter, cliquez sur **ajouter**. Pour sélectionner tous les modules, cliquez sur **sélectionner tout**. Pour effacer toutes les sélections, cliquez sur **Effacer tout**.  
  
5.  Une boîte de dialogue vous informe que les modules de la fonction ajoutée est visibles après avoir actualisé la **fonction Modules** nœud. Cliquez sur **OK**.  
  
6.  Avec le bouton droit le **fonction Modules** nœud et sélectionnez **Actualiser**. Les modules de la fonction sélectionnée s’affichent sous la **fonction Modules** nœud. Cliquez sur un nom de module de fonction pour afficher les propriétés dans le **propriétés** volet.  
  
7.  Développez un nom de module de fonction pour afficher les nœuds pour l’importation, exportation, modification et les paramètres de table.  
  
8.  Développez le **importer** nœud pour répertorier les paramètres d’importation pour le module de fonction. De même, développez le **exporter** et **Tables** nœuds pour afficher la liste des paramètres d’exportation et de table pour le module de fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)