---
title: "Comment déployer un adaptateur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f17b336c-6232-4889-ab7e-92b83fab0f5f
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e36443b99f01688a38e66a4a302ab64bb220092f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-custom-adapter"></a><span data-ttu-id="3a20b-102">Déploiement d'un adaptateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="3a20b-102">How to Deploy a Custom Adapter</span></span>
<span data-ttu-id="3a20b-103">Le processus complet d'installation d'un adaptateur est constitué des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a20b-103">A complete adapter installation process consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="3a20b-104">Vérifiez les dépendances.</span><span class="sxs-lookup"><span data-stu-id="3a20b-104">Check dependencies.</span></span> <span data-ttu-id="3a20b-105">Par exemple, le programme d'installation de l'adaptateur MSMQ vérifie l'existence du service MSMQ local car le composant d'exécution de l'adaptateur en dépend.</span><span class="sxs-lookup"><span data-stu-id="3a20b-105">For example, the MSMQ adapter installer checks for the existence of the local MSMQ service because the adapter runtime depends on it.</span></span>  
  
2.  <span data-ttu-id="3a20b-106">Configurez le système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="3a20b-106">Set up the local file system.</span></span> <span data-ttu-id="3a20b-107">Cela comprend la création de dossiers d'installation et la copie de fichiers binaire et de prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3a20b-107">This includes creating installation folders and copying binary and support files.</span></span> <span data-ttu-id="3a20b-108">Assurez-vous que l'accès aux dossiers et les autorisations d'accès aux fichiers sont configurés correctement.</span><span class="sxs-lookup"><span data-stu-id="3a20b-108">Ensure access to folders and file access permissions are configured properly.</span></span>  
  
3.  <span data-ttu-id="3a20b-109">Installez des assemblys managés dans le Global Assembly Cache du système.</span><span class="sxs-lookup"><span data-stu-id="3a20b-109">Install managed assemblies into the system global assembly cache.</span></span>  
  
4.  <span data-ttu-id="3a20b-110">Créez des clés de registre pour l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-110">Create registry keys for the adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a20b-111">Pour un adaptateur 32 bits, la console Administration de BizTalk Server utilise la branche HKEY_CLASSES_ROOT du registre pour obtenir la configuration personnalisée de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-111">For a 32-bit adapter, the BizTalk Server Administration Console uses the HKEY_CLASSES_ROOT branch in the registry to obtain custom adapter configuration.</span></span>  <span data-ttu-id="3a20b-112">Si un adaptateur 32 bits est installé sur un serveur 64 bits, la console Administration de BizTalk Server utilise alors la branche HKEY_CLASSES_ROOT\Wow6432Node\ pour les données de configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-112">If a 32-bit adapter is installed on a 64-bit server, the BizTalk Serve Administration Console instead uses the HKEY_CLASSES_ROOT\Wow6432Node\ branch for adapter configuration data.</span></span>  
  
5.  <span data-ttu-id="3a20b-113">Ajoutez l'adaptateur à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a20b-113">Add the adapter to BizTalk Server.</span></span> <span data-ttu-id="3a20b-114">Cela signifie que de nouvelles entrées de la base de données de gestion BizTalk pour l'adaptateur ainsi que pour le schéma de propriété sont utilisées pour refléter les propriétés promues par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-114">This means new entries in the BizTalk Management database for the adapter as well as for the property schema used to reflect properties the adapter promotes.</span></span> <span data-ttu-id="3a20b-115">Cette étape est parfois effectuée manuellement à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a20b-115">This step is sometimes done manually using the BizTalk Server Administration console.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="3a20b-116">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3a20b-116">Exceptions</span></span>  
 <span data-ttu-id="3a20b-117">Le programme d'installation de l'adaptateur ne doit pas obligatoirement vérifier les dépendances pour les installations partielles de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a20b-117">The adapter installer may not need to check the dependencies in partial BizTalk Server installations.</span></span> <span data-ttu-id="3a20b-118">Par exemple, pour une installation des outils d'administration uniquement, le programme d'installation de l'adaptateur n'est pas obligé de vérifier les dépendances du composant d'exécution de l'adaptateur car celui-ci n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="3a20b-118">For example, in an administration tools-only installation, the adapter installer does not need to check adapter runtime dependencies because the adapter runtime is not used.</span></span> <span data-ttu-id="3a20b-119">Cela est également valable pour une installation du composant d'exécution BizTalk Server uniquement, pour laquelle le programme d'installation de l'adaptateur n'est pas obligé de vérifier les dépendances du composant de conception de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-119">The same is true in the BizTalk Server runtime-only installation, where the adapter installer does not need to check the adapter design-time dependencies.</span></span>  
  
 <span data-ttu-id="3a20b-120">Dans les environnements BizTalk Server multi-serveurs, la dernière étape de la liste précédente (Ajout de l'adaptateur à BizTalk Server) se produit uniquement lors de l'installation de l'adaptateur sur le premier serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a20b-120">In multiple BizTalk Server environments, the last step in the preceding list (Add the adapter to BizTalk Server) only happens in the adapter installation on the first BizTalk Server.</span></span> <span data-ttu-id="3a20b-121">Cela est dû au fait que toutes les instances de service BizTalk Server  partagent la même base de données de gestion BizTalk (dotée du nom par défaut BizTalkMgmtDB).</span><span class="sxs-lookup"><span data-stu-id="3a20b-121">This is because all BizTalk Server service instances share the same BizTalk Management database (with the default name, BizTalkMgmtDB).</span></span> <span data-ttu-id="3a20b-122">Si des adaptateurs sont ajoutés à d'autres serveurs BizTalk du même groupe, les étapes suivantes échouent.</span><span class="sxs-lookup"><span data-stu-id="3a20b-122">If adapters are added to other BizTalk servers in the same group, the additional steps fail.</span></span>  
  
## <a name="install-the-adapter-assemblies-into-the-global-assembly-cache"></a><span data-ttu-id="3a20b-123">Installez les assemblys de l'adaptateur dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="3a20b-123">Install the Adapter Assemblies into the Global Assembly Cache</span></span>  
 <span data-ttu-id="3a20b-124">Pour une prise en charge de plusieurs environnements hôtes BizTalk Server avec différents chemins d'installation pour les adaptateurs, les assemblys d'adaptateur doivent être installés dans le Global Assembly Cache du système.</span><span class="sxs-lookup"><span data-stu-id="3a20b-124">To support multiple BizTalk Server host environments with different adapter installation paths, the adapter assemblies must be installed into the system global assembly cache.</span></span>  
  
 <span data-ttu-id="3a20b-125">Lors de l'installation et de la configuration de l'adaptateur, une nouvelle entrée d'adaptateur est créée dans la table adm_adapter de la base de données de gestion BizTalk (dotée du nom par défaut BizTalkMgmtDB).</span><span class="sxs-lookup"><span data-stu-id="3a20b-125">During the adapter installation and configuration, a new adapter entry is created in the adm_adapter table of the BizTalk Management database (with the default name BizTalkMgmtDB).</span></span> <span data-ttu-id="3a20b-126">Cette entrée contient toutes les données de référence utilisées par BizTalk Server pour le composant d'exécution et le composant de conception.</span><span class="sxs-lookup"><span data-stu-id="3a20b-126">This entry contains all reference information used by BizTalk Server for both run time and design time.</span></span>  
  
 <span data-ttu-id="3a20b-127">Le **InBoundAssemblyPath** et **OutboundAssemblyPath** champs sont utilisés par l’exécution de BizTalk Server pour savoir où charger les binaires de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-127">The **InBoundAssemblyPath** and **OutboundAssemblyPath** fields are used by the BizTalk Server runtime to find out where to load the adapter binaries.</span></span> <span data-ttu-id="3a20b-128">Étant donné qu'il n'y a qu'une base de données de gestion BizTalk par groupe BizTalk Server, tous les serveurs BizTalk du groupe doivent partager ces données.</span><span class="sxs-lookup"><span data-stu-id="3a20b-128">Because there is only one BizTalk Management database for a BizTalk Server group, all BizTalk servers in the group must share this same piece of information.</span></span> <span data-ttu-id="3a20b-129">Si vous voulez installer l'adaptateur sur différents serveurs BizTalk au sein du groupe, vous devez utiliser le même chemin d'installation sur chacun des serveurs.</span><span class="sxs-lookup"><span data-stu-id="3a20b-129">If you want to install the adapter on different BizTalk servers within the group, you must use the same installation path on each of those servers.</span></span> <span data-ttu-id="3a20b-130">Si le chemin d'installation local est différent du chemin stocké dans la base de données de gestion BizTalk, le serveur BizTalk Server ne peut pas charger les binaires de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-130">If the local installation path is different from the path stored in the BizTalk Management database, BizTalk Server cannot load the adapter binaries.</span></span>  
  
 <span data-ttu-id="3a20b-131">Signez toujours l'assembly de l'adaptateur avec un nom fort et utilisez Gacutil.exe pour placer l'assembly de l'adaptateur dans le Global Assembly Cache du système lors de l'installation de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-131">Always sign the adapter's assembly with a strong name and use Gacutil.exe to put the adapter assembly into the system global assembly cache during the adapter installation.</span></span> <span data-ttu-id="3a20b-132">Assurez-vous que vous laissez le **InBoundAssemblyPath** et **OutboundAssemblyPath** champs null ou vides.</span><span class="sxs-lookup"><span data-stu-id="3a20b-132">Make sure that you leave the **InBoundAssemblyPath** and **OutboundAssemblyPath** fields null, or empty.</span></span>  
  
## <a name="using-the-framework-for-adapter-configuration"></a><span data-ttu-id="3a20b-133">Utilisation de l'infrastructure de configuration de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="3a20b-133">Using the Framework for Adapter Configuration</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3a20b-134"> fournit une méthode permettant de générer des feuilles de propriétés pour l'interface utilisateur de configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-134"> provides a mechanism for generating property sheets for the adapter configuration user interface (UI).</span></span> <span data-ttu-id="3a20b-135">Ce mécanisme est basé sur une définition XSD (XML Schema Definition) des propriétés de configuration.</span><span class="sxs-lookup"><span data-stu-id="3a20b-135">It is based on an XML Schema Definition (XSD) definition of the configuration properties.</span></span> <span data-ttu-id="3a20b-136">L'utilisation de cette infrastructure présente des défis importants au développeur de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-136">The use of this framework introduces significant challenges for the adapter developer.</span></span> <span data-ttu-id="3a20b-137">Cette section suggère une solution efficace à certains de ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="3a20b-137">This section suggests an effective workaround for some of these issues.</span></span>  
  
### <a name="consider-custom-property-editors-for-all-your-key-properties"></a><span data-ttu-id="3a20b-138">Envisagez d'utiliser des éditeurs de propriétés personnalisées pour toutes vos principales propriétés.</span><span class="sxs-lookup"><span data-stu-id="3a20b-138">Consider Custom Property Editors for all Your Key Properties</span></span>  
 <span data-ttu-id="3a20b-139">Il est impossible d'appliquer une validation de propriété significative à des propriétés de la feuille de propriétés.</span><span class="sxs-lookup"><span data-stu-id="3a20b-139">It is impossible to put significant property validation on top of properties in the property sheet.</span></span> <span data-ttu-id="3a20b-140">L'infrastructure tente d'utiliser des restrictions simpletype XSD (XML Schema Definition) pour définir les règles de validation pour l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3a20b-140">The framework attempts to use XML Schema Definition (XSD) simpleType restrictions to define the validation rules for the UI.</span></span> <span data-ttu-id="3a20b-141">Les règles simples pour les valeurs maximum et minimum sont appliquées mais la restriction d'expression régulière pour les champs de type chaîne n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3a20b-141">The simple rules for maximum and minimum value are applied but the regular expression restriction for string fields is not supported.</span></span> <span data-ttu-id="3a20b-142">En outre, les données sont converties en types CLR (Common Language Runtime) avant l'application de la restriction.</span><span class="sxs-lookup"><span data-stu-id="3a20b-142">Also, the data is converted into common language runtime (CLR) types before the restriction is applied.</span></span> <span data-ttu-id="3a20b-143">Cela signifie que l'utilisateur de l'interface obtient parfois un message d'erreur énigmatique relatif à la conversion de type plutôt qu'un message d'erreur relatif à une valeur hors limite.</span><span class="sxs-lookup"><span data-stu-id="3a20b-143">This means the user of the UI sometimes gets a cryptic type-conversion error rather than an out-of-range error.</span></span> <span data-ttu-id="3a20b-144">Tout compte fait, la logique de validation est ténue.</span><span class="sxs-lookup"><span data-stu-id="3a20b-144">All in all, the validation logic is very weak.</span></span>  
  
 <span data-ttu-id="3a20b-145">La solution adoptée par de nombreux développeurs consiste à développer des éditeurs de propriétés personnalisées pour les propriétés principales de leur feuille de propriétés.</span><span class="sxs-lookup"><span data-stu-id="3a20b-145">The solution many adapter developers have adopted is to write custom property editors for the main properties on their property sheet.</span></span> <span data-ttu-id="3a20b-146">S'il existe plusieurs propriétés dépendantes les unes des autres, (ce qui est souvent le cas), l'éditeur de propriétés personnalisées peut combiner les résultats dans un seul champ et le composant d'exécution peut les séparer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="3a20b-146">If there are a number of cross-dependent properties (as is often the case), then the custom property editor can combine the results into a single field and the runtime can later separate them.</span></span> <span data-ttu-id="3a20b-147">Cette méthode est la seule qui permet d'insérer le code personnalisé obligatoire (bien qu'insignifiant) dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="3a20b-147">This is the only way to get the necessary (though still generally trivial) custom code into the interface.</span></span>  
  
 <span data-ttu-id="3a20b-148">Les éditeurs de propriétés personnalisées sont relativement faciles à développer et la propriété de la définition XSD peut être annotée pour faciliter leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="3a20b-148">Custom property editors are relatively straightforward to write and the property in the XSD can be annotated to use them.</span></span> <span data-ttu-id="3a20b-149">L'annotation fait référence à un assembly qui expose le point d'entrée de l'éditeur de propriété. En outre, elle est codée pour afficher un formulaire CLR.</span><span class="sxs-lookup"><span data-stu-id="3a20b-149">The annotation references an assembly that exposes the property editor entry point, and it is coded to show a CLR Form.</span></span> <span data-ttu-id="3a20b-150">Vous pouvez maintenant développer une interface utilisateur normale et utiliser les outils de génération d'interface traditionnels proposés par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a20b-150">You can now write a regular user interface and use the traditional interface-generation tools that Visual Studio offers.</span></span>  
  
 <span data-ttu-id="3a20b-151">L'exemple de code suivant illustre l'utilisation de la définition XSD pour ajouter un éditeur de propriétés personnalisées :</span><span class="sxs-lookup"><span data-stu-id="3a20b-151">The following code shows how to use the XSD to add a custom property editor:</span></span>  
  
```  
<xs:element name="queueDetails" type="xs:string" minOccurs="0">  
    <xs:annotation>  
        <xs:appinfo>  
           <baf:designer>  
               <baf:displayname _locID="queueName">Queue Definition</baf:displayname>  
               <baf:description _locID="receiveQueueDesc">Details of MQSeries Server, Queue Manager and Queue from where you want to receive messages.</baf:description>  
               <baf:category _locID="mqsCategory">MQSeries</baf:category>  
               <baf:editor assembly="Microsoft.BizTalk Server.Adapter.MQSAdmin.dll">Microsoft.BizTalk Server.Adapter.MQSAdmin.MQSUITypeEditor</baf:editor>  
            </baf:designer>  
        </xs:appinfo>  
    </xs:annotation>  
</xs:element>  
  
```  
  
 <span data-ttu-id="3a20b-152">Le code référencé doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="3a20b-152">The code that is referenced should look like this:</span></span>  
  
```  
public class MQSUITypeEditor : System.Drawing.Design.UITypeEditor  
{  
public override System.Drawing.Design.UITypeEditorEditStyle GetEditStyle  
(System.ComponentModel.ITypeDescriptorContext context)   
{  
return System.Drawing.Design.UITypeEditorEditStyle.Modal;  
}  
public override object EditValue (System.ComponentModel.ITypeDescriptorContext context,  
System.IServiceProvider provider, object value)   
{  
Form qdForm = new QueueDefinitionForm(value);  
IWindowsFormsEditorService service =   
(IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));  
DialogResult dialogResult = service.ShowDialog(qdForm);  
//…  
}  
}  
class QueueDefinitionForm : System.Windows.Forms.Form   
{  
//  traditional UI code goes here!  
}  
  
```  
  
 <span data-ttu-id="3a20b-153">Le composant d'administration doit être en mesure de trouver l'assembly référencé dans la définition XSD. Vous devez donc l'ajouter au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="3a20b-153">The administration runtime must be able to find the assembly referenced in the XSD, so you should add it to the global assembly cache.</span></span>