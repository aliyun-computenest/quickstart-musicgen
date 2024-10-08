<h1>MusicGen Community Edition </h1>

<h2> Overview </h2>

<p>MusicGen is a large model for generating high-quality audio developed based on the AudioCraft library. It is a simple, controllable music generation model that can generate high-quality music given a text description. MusicGen can generate consistent music with a single-stage language model through an effective codebook interleaving strategy, and can perform text and melody conditional generation. </p>

<h2> Instance Description </h2>

<p>MusicGen is deployed based on the community open source version, refer to the source code <a href = "https://github.com/facebookresearch/audiocraft">audiocraft</a>. The instance specification packages are as follows:</p>

<table>
<thead>
<tr>
<th> Specification family </th>
<th>vCPU and memory </th>
<th> System disk </th>
</tr>
</thead>
<tbody>
<tr>
<td>ecs.gn6i-*</td>
<td>T4 GPU computing </td>
<td>ESSD 60GiB PL0</td>
</tr>
<tr>
<td>ecs.gn7i-*</td>
<td>T4 GPU computing </td>
<td>ESSD 60GiB PL0</td>
</tr>
</tbody>
</table>

<h2> Description </h2>

<p> Depending on your instance type and region, the music generation process may take several minutes to ten minutes. Please click Submit and wait patiently </p>

<h2> Deployment process </h2>

<h3>0. Preparations </h3>

<p> Before you start using it, you need an Alibaba Cloud account to access and create resources such as ECS and VPC.
-If you use a personal account, you can directly create a service instance.
-If you use a RAM user to create a service instance and this is the first time you use Alibaba Cloud Compute
-- Before creating a service instance, you must add the corresponding resource permissions to the account of the RAM user. For more information about how to add RAM permissions, see <a href = "https://help.aliyun.com/zh/ram/getting-started/grant-permissions-to-a-ram-user"> Authorize RAM users </a>. The required permissions are shown in the following table.
-- and you need to authorize the creation of associated roles, refer to the following figure, select agree to authorize and create associated roles </p>

<table>
<thead>
<tr>
<th> Permission policy name </th>
<th> Remarks </th>
</tr>
</thead>
<tbody>
<tr>
<td>AliyunECSFullAccess</td>
<td> Permissions to manage ECS </td>
</tr>
<tr>
<td>AliyunVPCFullAccess</td>
<td> Permissions for managing VPC networks </td>
</tr>
<tr>
<td>AliyunROSFullAccess</td>
<td> Manage permissions for Resource Orchestration Services (ROS) </td>
</tr>
<tr>
<td>AliyunComputeNestUserFullAccess</td>
<td> Manage user-side permissions for the compute nest service (ComputeNest) </td>
</tr>
</tbody>
</table>

<p><img src="1.png" alt="1.png" /></p>

<h3>1. Deployment portal </h3>

<p> you can log on to <a href = "https://computenest.console.aliyun.com/user/cn-hangzhou/recommendService"> alibaba cloud-welcome to alibaba cloud, a secure and stable cloud computing service platform </a> alibaba cloud computing nest, or you can quickly reach it through the following deployment link. </p>

<p><a href = "https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?ServiceId=service-e56ef773412e412a9300"> Deployment link </a></p>

<h3>2. Create a service </h3>

<h4>2.1 parameter list </h4>

<p> In the process of creating a service instance, you need to configure the parameter list of service instance information, as follows:</p>

<table>
<thead>
<tr>
<th> Parameter group </th>
<th> Parameter item </th>
<th> Example </th>
<th> Description </th>
</tr>
</thead>
<tbody>
<tr>
<td> Service instance name </td>
<td>N/A</td>
<td>MusicGen-mc64</td>
<td> Name of the instance </td>
</tr>
<tr>
<td> Region </td>
<td>N/A</td>
<td> Singapore </td>
<td> Select the region of the service instance. We recommend that you select the region nearby to obtain better network latency. </td>
</tr>
<tr>
<td> Payment type configuration </td>
<td> Payment type </td>
<td> Pay-As-You-Go </td>
<td>N/A</td>
</tr>
<tr>
<td> Availability Zone and Basic Resource Configuration </td>
<td> Switch subnet segment </td>
<td>192.168.1.0/24</td>
<td> The switch subnet segment must belong to the IPV4 subnet segment of the VPC. </td>
</tr>
<tr>
<td> Availability Zone and Basic Resource Configuration </td>
<td> Switch zone </td>
<td> Availability Zone I</td>
<td> Different available regions under the region, make sure that the instance is not empty. </td>
</tr>
<tr>
<td> Availability Zone and Basic Resource Configuration </td>
<td> IPV4 segment of VPC </td>
<td>192.168.0.0/16</td>
<td> the ip address range of the VPC. you can use the following ip address range or its subnet: 10.0.0.0/8,172.16.0.0/12,192.168.0.0/16</td>
</tr>
<tr>
<td> Service instance configuration </td>
<td> Instance type </td>
<td>ecs.gn6i-c8g1.2xlarge</td>
<td> Select T4 GPU package specifications or custom package specifications </td>
</tr>
<tr>
<td> Service instance configuration </td>
<td> System disk space </td>
<td>100</td>
<td> System disk size, which can be set to 500 at the maximum and 60 at the minimum. </td>
</tr>
<tr>
<td> Service instance configuration </td>
<td> Instance password </td>
<td><strong>**</strong></td>
<td> Set the instance password. It must contain three items (uppercase letters, lowercase letters, numbers, special symbols in ()'~!@#$%^& *_-+ ={}[]:;' <>,.?/). </td>
</tr>
</tbody>
</table>

<h4>2.2 steps </h4>

<p> You can search on your own in the Alibaba Cloud computing nest, or you can quickly reach it through the following deployment link.
Create a service according to the following steps, refer to the following figure:
-Fill in the instance name, such as "MusicGen-mc64"
-Select a region, such as "Singapore"
-Select payment type
-Select Switch Availability Zone
-Edit the IPV4 network segment of the private network, there are three network segments for you to choose </p>

<p><img src="2.png" alt="2.png" /></p>

<ul>
<li> Edit the switch subnet CIDR block. The switch subnet CIDR block must belong to IPV4 CIDR block </li>
</ul>

<p><img src="3.png" alt="3.png" /></p>

<ul>
<li> Select the instance type, and we set the default value for you. If the list is gray and cannot be selected, change to an availability zone or another region. </li>
</ul>

<p><img src="4.png" alt="4.png" /></p>

<ul>
<li> editing system disk space requires at least 60G and can be set to 500G at most </li>
<li> Edit instance password </li>
</ul>

<p><img src="5.png" alt="5.png" /></p>

<ul>
<li> Click Next to enter the order confirmation page </li>
<li> Check the check boxes in Permission Confirmation and Terms of Service </li>
<li> Click Create Now </li>
</ul>

<p><img src="6.png" alt="6.png" /></p>

<h3>3. Start the MusicGen service </h3>

<ul>
<li> On the Service Instance Management page, wait for the Deployment Status to change to Deployed ". </li>
</ul>

<p><img src="7.png" alt="7.png" /></p>

<ul>
<li> Click the service instance to access the service instance details. </li>
<li> Click Endpoint</li>
</ul>

<p><img src="8.png" alt="8.png" /></p>

<ul>
<li> enter the editing interface, you can upload pictures in the input image </li>
</ul>

<p><img src="9.png" alt="9.png" /></p>

<ul>
<li> Click submit to generate music on the right </li>
</ul>

<p><img src="10.png" alt="10.png" /></p>

<ul>
<li> You can adjust the Duration to control the length of the generated music, up to 30 seconds </li>
</ul>

<p> Finally, please try to play with your imagination. Have any ideas or suggestions or cooperation needs, please contact us ~~~</p>
