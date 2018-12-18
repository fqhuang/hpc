# HPC和公有云<a name="ZH-CN_TOPIC_0062552881"></a>

## 公有云上部署HPC的优势<a name="section5593597204121"></a>

传统的HPC使用中存在如下问题：

-   投资成本高，扩容部署复杂，重复利用已有投资十分困难。
-   应用复杂，资源预测困难，灵活性差，亟待提升效率。
-   效率低下导致决策缓慢，失去市场、以及开发研究成果的良机。
-   应用计算量快速膨胀，对性能要求越来越高。

公有云上应用HPC场景，能充分利用云服务的优势。使用公有云进行高性能计算具有以下优势：

-   降低TCO

    可以按需租用，成本低，降低中小客户使用HPC的门槛。

-   提高效率

    按需发放，快速部署与扩容，加速产品上市时间和缩短科研周期。

-   使用灵活
    -   在镜像模板中预制MPI库、编译库及优化配置，加快环境部署。
    -   企业分支、科研组织机构等跨全球地理位置进行及时协同工作，提高效率。
    -   可以利用公有云的跨地域能力，共享计算资源，海量数据，并能实现云端大数据分析。

-   优化性能
    -   性能比普通云服务器提高30%。
    -   通过虚拟化优化（SR-IOV、PCI直通）等，各类测试报告显示：大规模云化HPC性能损耗不大。


## HPC与云服务的关系<a name="section1879885620425"></a>

**表 1**  所需云服务

<a name="table176034915038"></a>
<table><thead align="left"><tr id="row2426907715038"><th class="cellrowborder" valign="top" width="33.09%" id="mcps1.2.3.1.1"><p id="p4252615315038"><a name="p4252615315038"></a><a name="p4252615315038"></a>云服务</p>
</th>
<th class="cellrowborder" valign="top" width="66.91%" id="mcps1.2.3.1.2"><p id="p2206633015038"><a name="p2206633015038"></a><a name="p2206633015038"></a>作用</p>
</th>
</tr>
</thead>
<tbody><tr id="row6437924515038"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p4733638215038"><a name="p4733638215038"></a><a name="p4733638215038"></a>弹性云服务器（ECS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p904177215038"><a name="p904177215038"></a><a name="p904177215038"></a>用于在公有云平台上创建高性能计算服务器。</p>
</td>
</tr>
<tr id="row1426708915038"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p1478357315038"><a name="p1478357315038"></a><a name="p1478357315038"></a>虚拟私有云（VPC）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p5661872815038"><a name="p5661872815038"></a><a name="p5661872815038"></a>HPC场景下所涉及的云服务器，都位于同一个VPC中，并且需要使用VPC中的子网和安全组的相关网络安全隔离。</p>
</td>
</tr>
<tr id="row3980651215038"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p310204815038"><a name="p310204815038"></a><a name="p310204815038"></a>镜像服务（IMS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><a name="ul56700982152237"></a><a name="ul56700982152237"></a><ul id="ul56700982152237"><li>在创建高性能计算的云服务器时，需要使用符合要求的镜像文件。</li><li>在制作私有镜像时，需要将已有的高性能计算云服务器创建为私有镜像，从而创建集群使用。</li></ul>
</td>
</tr>
<tr id="row4680066315038"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p3275737315038"><a name="p3275737315038"></a><a name="p3275737315038"></a>云硬盘（EVS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p3610156315038"><a name="p3610156315038"></a><a name="p3610156315038"></a>HPC场景下使用的弹性云服务器，均绑定了云硬盘。</p>
</td>
</tr>
<tr id="row37049103193922"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p65006474193922"><a name="p65006474193922"></a><a name="p65006474193922"></a>裸金属服务器（BMS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p31033033193922"><a name="p31033033193922"></a><a name="p31033033193922"></a>为用户提供专属的物理服务器，提供卓越的计算性能，满足核心应用对高性能及稳定性的需求，结合了传统托管服务器的稳定性与云中资源高度弹性的优势。</p>
</td>
</tr>
<tr id="row57649311193922"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p49081752193922"><a name="p49081752193922"></a><a name="p49081752193922"></a>对象存储服务（OBS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p16198981193922"><a name="p16198981193922"></a><a name="p16198981193922"></a>是一种基于对象的海量存储服务，为用户提供海量、低成本、高可靠、高安全的数据存储能力。</p>
</td>
</tr>
<tr id="row56914348193922"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p42467084193922"><a name="p42467084193922"></a><a name="p42467084193922"></a>弹性文件服务（SFS）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p17281809193922"><a name="p17281809193922"></a><a name="p17281809193922"></a>为用户的弹性云服务器提供一个完全托管的共享文件存储，符合标准文件协议( NFS )，能够弹性伸缩至PB规模，具备可扩展的性能，为海量数据、高带宽型应用提供有力支持。</p>
</td>
</tr>
<tr id="row17829153193922"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p26244650193922"><a name="p26244650193922"></a><a name="p26244650193922"></a>数据快递服务（DES）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p45441888193922"><a name="p45441888193922"></a><a name="p45441888193922"></a>是一种海量数据传输服务，它使用物理存储介质（USB或eSATA接口）向华为公有云传输大量数据。解决了海量数据在互联网上传输的难题（高昂网络带宽成本、较长传输时间等）。</p>
</td>
</tr>
<tr id="row62973186194034"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p29887768194034"><a name="p29887768194034"></a><a name="p29887768194034"></a>虚拟专用网络（VPN）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p4990177194034"><a name="p4990177194034"></a><a name="p4990177194034"></a>是在用户的其他数据中心和公有云之间建立的一条符合行业标准的安全加密通信隧道，可将已有数据中心无缝扩展到公有云上。</p>
</td>
</tr>
<tr id="row625001194034"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p5625017194034"><a name="p5625017194034"></a><a name="p5625017194034"></a>云专线（DC）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p52973229194034"><a name="p52973229194034"></a><a name="p52973229194034"></a>用于搭建企业自有数据中心到华为公有云的高速、稳定、安全的专属连接通道，充分利用公有云服务优势的同时，继续使用现有的IT设施，实现灵活一体，可伸缩的混合云计算环境。</p>
</td>
</tr>
<tr id="row49395471194034"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p41906057194034"><a name="p41906057194034"></a><a name="p41906057194034"></a>云监控服务（CES）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p38947427194034"><a name="p38947427194034"></a><a name="p38947427194034"></a>为用户提供一个针对弹性云服务器、带宽等资源的立体化监控平台。给用户提供实时监控告警、通知以及个性化报表视图，精准掌握产品资源状态。</p>
</td>
</tr>
<tr id="row35390814194126"><td class="cellrowborder" valign="top" width="33.09%" headers="mcps1.2.3.1.1 "><p id="p32847853194131"><a name="p32847853194131"></a><a name="p32847853194131"></a>云桌面（Workspace）</p>
</td>
<td class="cellrowborder" valign="top" width="66.91%" headers="mcps1.2.3.1.2 "><p id="p30099699194126"><a name="p30099699194126"></a><a name="p30099699194126"></a>是一种由华为公有云提供的虚拟Windows桌面与应用的服务，用户可随时随地接入云桌面办公。云桌面服务提供专业的办公应用，帮助用户打造更精简、更安全、更低维护成本、更高服务效率的IT办公系统。</p>
</td>
</tr>
</tbody>
</table>

