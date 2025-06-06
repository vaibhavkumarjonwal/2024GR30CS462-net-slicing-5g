Lab Project
Network Slicing in 5g Drones






2024GR37CS462
Vaibhav Kumar Jonwal
202251150
Azim Khorajiya
202251169
Yash Hire
202252319
Sakshi Dhoni
202252335
Nihalmayi
202251149
# Contents
NS-3 (Setup)
Installation
Download NS-3
Installing Dependencies
Building NS-3
NetSimulyzer (Setup)
Installation
Downloading NetSimulyzer NS-3 module
Installing Dependencies
Building NS-3 for NetSimulyzer
Installing NetSimulyzer Software
Drone Simulation
Setup Code & Simulation
Write Code
Running Simulation
5G Integration
Setup Code
5G-LENA Setup
Write Code
Slicing Integration
Setup Code
Write Code
Running Simulation
All Simulations

# NS-3 Setup
# Installation
### Downloading NS-3
(We will use ns-3.42 for compatibility with 5g-lena)
Step1: Go to Link:
Step2: Click on  or from website as shown in the below image to download the zipped file from the ns3 website.
![image](images/image1.png)


Step3: Make your project directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
mkdir project



Step4: Move the file to your project directory
(Consider we are at /username directory)
Go to Terminal:
cd Downloads
mv ns-allinone-3.42.tar.bz2 ~/Desktop/project



Step5: Go to project Directory and extract the file
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
sudo apt update && sudo apt install bzip2

tar -xvjf ns-allinone-3.42.tar.bz2

### Install Dependencies
Install all the dependencies required to build
(Consider we are at /username directory)
Go to Terminal:
sudo apt install g++ python3 cmake ninja-build git gir1.2-goocanvas-2.0 python3-gi python3-gi-cairo python3-pygraphviz gir1.2-gtk-3.0 ipython3 tcpdump wireshark sqlite3 libsqlite3-dev qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools openmpi-bin openmpi-common openmpi-doc libopenmpi-dev doxygen graphviz imagemagick python3-sphinx dia texlive dvipng latexmk texlive-extra-utils texlive-latex-extra texlive-font-utils libeigen3-dev gsl-bin libgsl-dev libgslcblas0 libxml2 libxml2-dev libgtk-3-dev lxc-utils lxc-templates vtun uml-utilities ebtables bridge-utils libboost-all-dev ccache

(Type Y and continue to Download)


(Opt any option as per your preference)

(Wait until the progress hits 100%)

#### Building NS-3
Step1: Go to ns-allinone-3.42 directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
cd ns-allinone-3.42

Step2: Build NS-3
(Consider we are at /ns-allinone-3.42 directory)
Go to Terminal:
./build.py --enable-examples --enable-tests


(Wait until it completes 1940/1940)

Step3: Check the Built
(Consider we are at /ns-allinone-3.42 directory)
Go to Terminal:
cd ns-3.42
./ns3 run hello-simulator

(It is showing Hello Simulator)

# NetSimulyzer Setup
# Installation
### Downloading NetSimulyzer NS-3 module
Step1: Go to /contrib directory
(Consider we are at /ns-3.42 directory)
Go to Terminal:
cd contrib



Step2: Go to /contrib directory
(Consider we are at /ns-3.42 directory)
Go to Terminal:
wget https://github.com/usnistgov/NetSimulyzer-ns3-module/archive/master.zip -O NetSimulyzer-ns3-module-master.zip

Step3: Unzip downloaded file
(Consider we are at /contrib directory)
Go to Terminal:
unzip NetSimulyzer-ns3-module-master.zip

Step3: Rename the resulting directory to netsimulyze
(As ns-3 will not accept a module named differently than its directory.)
(Consider we are at /contrib directory)
Go to Terminal:
mv NetSimulyzer-ns3-module-master netsimulyzer


### Install Dependencies
Install all dependencies for NetSimulyzer
(Consider we are at /username directory)
Go to Terminal:
sudo apt install cmake pkg-config qtbase5-dev libqt5charts5-dev g++ python3 cmake ninja-build git gir1.2-goocanvas-2.0 python3-gi python3-gi-cairo python3-pygraphviz gir1.2-gtk-3.0 ipython3 tcpdump wireshark sqlite3 libsqlite3-dev qtchooser qt5-qmake qtbase5-dev-tools openmpi-bin openmpi-common openmpi-doc libopenmpi-dev doxygen graphviz imagemagick python3-sphinx dia texlive dvipng latexmk texlive-extra-utils texlive-latex-extra texlive-font-utils libeigen3-dev gsl-bin libgsl-dev libgslcblas0 libxml2 libxml2-dev libgtk-3-dev lxc-utils lxc-templates vtun uml-utilities ebtables bridge-utils libboost-all-dev

(Press Y to continue)

#### Building NS-3 for NetSimulyzer
Step1: Go to ns-allinone-3.42 directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
cd ns-allinone-3.42

Step2: Build NS-3
(Consider we are at /ns-allinone-3.42 directory)
Go to Terminal:
./build.py --enable-examples --enable-tests


(Wait until it completes 53/53)

Step3: Check the Built
(Consider we are at /ns-allinone-3.42 directory)
Go to Terminal:
cd ns-3.42
./ns3 run contrib/netsimulyzer/examples mobility-buildings-example.cc



Installing NetSimulyzer Software
Step1: Go to project directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project

Step2: Clone the NetSimulyzer Repo
(Consider we are at /project directory)
Go to Terminal:
clone --recursive https://github.com/usnistgov/NetSimulyzer.git

Step3: Make /build directory
(Consider we are at /project directory)
Go to Terminal:
cd NetSimulyzer
mkdir build
cd build

Step4: Build Software
(Consider we are at /build directory)
Go to Terminal:
cmake -DCMAKE_BUILD_TYPE=Release ..

(Error Occurred, we will solve the error by installing required dependencies)
sudo apt install libassimp-dev

sudo apt install qt6-base-dev qt6-base-dev-tools

(Now Again)
cmake -DCMAKE_BUILD_TYPE=Release ..

cmake --build .

(Wait until the build)



Step5: Check NetSimulyzer
(Consider we are at /build directory)
Go to Terminal:
cd NetSimulyzer
./netsimulyzer







# Drone Simulation
# Setup Code & Simulation
### Write Code
Step1: Go to /scratch directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
cd ns-allinone-3.42
cd ns-3.42
cd scratch



Code
#include "ns3/aodv-module.h"
#include "ns3/core-module.h"
#include "ns3/internet-module.h"
#include "ns3/mobility-module.h"
#include "ns3/network-module.h"
#include "ns3/ping-helper.h"
#include "ns3/point-to-point-module.h"
#include "ns3/yans-wifi-helper.h"
#include <ns3/netsimulyzer-module.h>
#include <cmath>
#include <iostream>

using namespace ns3;

/**
* @defgroup aodv-examples AODV Examples
* @ingroup aodv
* @ingroup examples
*/

/**
* @ingroup aodv-examples
* @ingroup examples
* @brief Test script.
*
* This script creates 1-dimensional grid topology and then ping last node from the first one:
*
* [10.0.0.1] <-- step --> [10.0.0.2] <-- step --> [10.0.0.3] <-- step --> [10.0.0.4]
*
* ping 10.0.0.4
*
* When 1/3 of simulation time has elapsed, one of the nodes is moved out of
* range, thereby breaking the topology.  By default, this will result in
* stopping ping replies reception after sequence number 33. If the step size is reduced
* to cover the gap, then also the following pings can be received.
*/
class AodvExample
{
public:
AodvExample();
/**
* @brief Configure script parameters
* @param argc is the command line argument count
* @param argv is the command line arguments
* @return true on successful configuration
*/
bool Configure(int argc, char** argv);
/// Run simulation
void Run();
/**
* Report results
* @param os the output stream
*/
void Report(std::ostream& os);

private:
// parameters
/// Number of nodes
uint32_t size;
/// Distance between nodes, meters
double step;
/// Simulation time, seconds
double totalTime;
/// Write per-device PCAP traces if true
bool pcap;
/// Print routes if true
bool printRoutes;

// network
/// nodes used in the example
NodeContainer nodes;
/// devices used in the example
NetDeviceContainer devices;
/// interfaces used in the example
Ipv4InterfaceContainer interfaces;

private:
/// Create the nodes
void CreateNodes();
/// Create the devices
void CreateDevices();
/// Create the network
void InstallInternetStack();
/// Create the simulation applications
void InstallApplications();
};

int
main(int argc, char** argv)
{
AodvExample test;
if (!test.Configure(argc, argv))
{
NS_FATAL_ERROR("Configuration failed. Aborted.");
}

test.Run();
test.Report(std::cout);
return 0;
}

//-----------------------------------------------------------------------------
AodvExample::AodvExample()
: size(10),
step(5),
totalTime(100),
pcap(true),
printRoutes(true)
{
}

bool
AodvExample::Configure(int argc, char** argv)
{
// Enable AODV logs by default. Comment this if too noisy
// LogComponentEnable("AodvRoutingProtocol", LOG_LEVEL_ALL);

SeedManager::SetSeed(12345);
CommandLine cmd(__FILE__);

cmd.AddValue("pcap", "Write PCAP traces.", pcap);
cmd.AddValue("printRoutes", "Print routing table dumps.", printRoutes);
cmd.AddValue("size", "Number of nodes.", size);
cmd.AddValue("time", "Simulation time, s.", totalTime);
cmd.AddValue("step", "Grid step, m", step);

cmd.Parse(argc, argv);
return true;
}

void
AodvExample::Run()
{
//  Config::SetDefault ("ns3::WifiRemoteStationManager::RtsCtsThreshold", UintegerValue (1)); //
//  enable rts cts all the time.
CreateNodes();
CreateDevices();
InstallInternetStack();
InstallApplications();

std::cout << "Starting simulation for " << totalTime << " s ...\n";
//  AnimationInterface anim("testing.xml");
Simulator::Stop(Seconds(totalTime));
Simulator::Run();
Simulator::Destroy();
}

void
AodvExample::Report(std::ostream&)
{
}

void
AodvExample::CreateNodes()
{
auto orchestrator = CreateObject<netsimulyzer::Orchestrator> ("testing.json");
netsimulyzer::NodeConfigurationHelper nodeHelper{orchestrator};
nodeHelper.Set ("Model", netsimulyzer::models::QUADCOPTER_UAV_VALUE);

// Shows every Node in the scenario
for (auto node = NodeList::Begin (); node != NodeList::End (); node++)
nodeHelper.Install (*node);
std::cout << "Creating " << (unsigned)size << " nodes " << step << " m apart.\n";
nodes.Create(size);
// Name nodes
for (uint32_t i = 0; i < size; ++i)
{
std::ostringstream os;
os << "node-" << i;
Names::Add(os.str(), nodes.Get(i));
}
nodeHelper.Install (nodes);
// Create static grid
MobilityHelper mobility;
mobility.SetPositionAllocator("ns3::GridPositionAllocator",
"MinX",
DoubleValue(0.0),
"MinY",
DoubleValue(0.0),
"Z",
DoubleValue(15.0),
"DeltaX",
DoubleValue(step),
"DeltaY",
DoubleValue(0),
"GridWidth",
UintegerValue(size),
"LayoutType",
StringValue("RowFirst"));

mobility.SetMobilityModel("ns3::GaussMarkovMobilityModel"),
"Bounds", BoxValue(Box(-5, 5, -5, 5, 0, 15)),
"TimeStep", TimeValue(Seconds(0.05)),
"Alpha", DoubleValue(0.85),
"MeanVelocity", StringValue("ns3::UniformRandomVariable[Min=5|Max=20]"),
"MeanDirection", StringValue("ns3::UniformRandomVariable[Min=0|Max=6.283185307]"),
"MeanPitch", StringValue("ns3::UniformRandomVariable[Min=0.05|Max=0.05]"),
"NormalVelocity", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.0|Bound=0.0]"),
"NormalDirection", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.2|Bound=0.4]"),
"NormalPitch", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.02|Bound=0.04]");


mobility.Install(nodes);
}

void
AodvExample::CreateDevices()
{
WifiMacHelper wifiMac;
wifiMac.SetType("ns3::AdhocWifiMac");
YansWifiPhyHelper wifiPhy;
YansWifiChannelHelper wifiChannel = YansWifiChannelHelper::Default();
wifiPhy.SetChannel(wifiChannel.Create());
WifiHelper wifi;
wifi.SetRemoteStationManager("ns3::ConstantRateWifiManager",
"DataMode",
StringValue("OfdmRate6Mbps"),
"RtsCtsThreshold",
UintegerValue(0));
devices = wifi.Install(wifiPhy, wifiMac, nodes);

if (pcap)
{
wifiPhy.EnablePcapAll(std::string("aodv"));
}
}

void
AodvExample::InstallInternetStack()
{
AodvHelper aodv;
// you can configure AODV attributes here using aodv.Set(name, value)
InternetStackHelper stack;
stack.SetRoutingHelper(aodv); // has effect on the next Install ()
stack.Install(nodes);
Ipv4AddressHelper address;
address.SetBase("10.0.0.0", "255.0.0.0");
interfaces = address.Assign(devices);

if (printRoutes)
{
Ptr<OutputStreamWrapper> routingStream =
Create<OutputStreamWrapper>("aodv.routes", std::ios::out);
Ipv4RoutingHelper::PrintRoutingTableAllAt(Seconds(8), routingStream);
}
}

void
AodvExample::InstallApplications()
{
PingHelper ping(interfaces.GetAddress(size - 1));
ping.SetAttribute("VerboseMode", EnumValue(Ping::VerboseMode::VERBOSE));

ApplicationContainer p = ping.Install(nodes.Get(0));
p.Start(Seconds(0));
p.Stop(Seconds(totalTime) - Seconds(0.001));

// move node away
Ptr<Node> node = nodes.Get(size / 2);
Ptr<MobilityModel> mob = node->GetObject<MobilityModel>();
Simulator::Schedule(Seconds(totalTime / 3),
&MobilityModel::SetPosition,
mob,
Vector(1e5, 1e5, 1e5));
}





Step2: Write code
(Consider we are at /scratch directory)
Go to Terminal:
nano test.cc

(Paste the code provided above)
Press: Ctrl+x
Write: Y
Press: Enter


Step2: Run Code
(Consider we are at /scratch directory)
Go to Terminal:
cd ..
./ns3 run scratch/test.cc


(Now we can find there is a testing.json file in the /ns-3.42 directory)

### Running Simulation
Step1: Run NetSimulyzer
(Consider we are at /username directory)
Go to Terminal:
cd Desktop/project/NetSimulyzer/build
./netsimulyzer

Step2: Load The testing.json File


(Open)

Step3: Play the simulation










# 5g Integration
# Setup Code
### 5G-LENA Setup
Step1: Go to /contrib directory & Clone nr repo
(Consider we are at /username directory)
Go to Terminal:
cd Desktop/project/ns-allinone-3.42/ns-3.42/contrib
git clone https://gitlab.com/cttc-lena/nr.git

Step2: Configure
(Consider we are at /contrib directory)
Go to Terminal:
cd ..
./ns3 configure --enable-examples --enable-tests

Step3: Build
(Consider we are at /ns-3.42 directory)
Go to Terminal:
cd ..
./build.py –enable-examples –enable-tests

### Write Code
Step1: Go to /scratch directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
cd project
cd ns-allinone-3.42
cd ns-3.42/scratch

Step2: Write code
(Consider we are at /scratch directory)
Go to Terminal:
nano test5g.cc

(Paste the code provided below)
Press: Ctrl+x
Write: Y
Press: Enter


Code
#include "ns3/aodv-module.h"
#include "ns3/core-module.h"
#include "ns3/internet-module.h"
#include "ns3/mobility-module.h"
#include "ns3/network-module.h"
#include "ns3/ping-helper.h"
#include "ns3/point-to-point-module.h"
// Remove WiFi headers
// #include "ns3/yans-wifi-helper.h"
// Add 5G NR headers
#include "ns3/nr-module.h"
#include "ns3/eps-bearer-tag.h"
#include "ns3/lte-module.h"
#include <ns3/netsimulyzer-module.h>
#include <cmath>
#include <iostream>

using namespace ns3;

/**
* @brief Drone simulation with 5G connectivity.
*
* This script creates a 5G network with drones as UEs (User Equipment)
* and a gNB (5G base station).
*/
class DroneWith5GExample
{
public:
DroneWith5GExample();
bool Configure(int argc, char** argv);
void Run();
void Report(std::ostream& os);

private:
// parameters
uint32_t numDrones;  	// Number of drone UEs
double simTime;      	// Simulation time in seconds
bool pcap;           	// Write PCAP traces if true
bool printRoutes;    	// Print routing tables if true
double gNbHeight;    	// Height of the gNB in meters
double droneMinHeight;   // Minimum height of drones in meters
double droneMaxHeight;   // Maximum height of drones in meters
double areaSizeX;    	// X dimension of the simulation area
double areaSizeY;    	// Y dimension of the simulation area

// network
NodeContainer droneUEs;       	// Drone nodes acting as UEs
NodeContainer gNbNodes;       	// gNB nodes (base stations)
NetDeviceContainer ueDevices; 	// UE devices
NetDeviceContainer gNbDevices;	// gNB devices
Ipv4InterfaceContainer ueIfaces;  // UE interfaces
Ipv4InterfaceContainer gNbIfaces; // gNB interfaces

private:
void CreateNodes();
void ConfigureMobility();
void Install5GDevices();
void InstallInternetStack();
void InstallApplications();
};

int
main(int argc, char** argv)
{
DroneWith5GExample test;
if (!test.Configure(argc, argv))
{
NS_FATAL_ERROR("Configuration failed. Aborted.");
}

test.Run();
test.Report(std::cout);
return 0;
}

//-----------------------------------------------------------------------------
DroneWith5GExample::DroneWith5GExample()
: numDrones(10),
simTime(100),
pcap(true),
printRoutes(true),
gNbHeight(30.0),
droneMinHeight(10.0),
droneMaxHeight(50.0),
areaSizeX(500.0),
areaSizeY(500.0)
{
}

bool
DroneWith5GExample::Configure(int argc, char** argv)
{
SeedManager::SetSeed(12345);
CommandLine cmd(FILE);

cmd.AddValue("pcap", "Write PCAP traces.", pcap);
cmd.AddValue("printRoutes", "Print routing table dumps.", printRoutes);
cmd.AddValue("numDrones", "Number of drone UEs.", numDrones);
cmd.AddValue("simTime", "Simulation time, s.", simTime);
cmd.AddValue("gNbHeight", "Height of gNB, m.", gNbHeight);
cmd.AddValue("droneMinHeight", "Minimum height of drones, m.", droneMinHeight);
cmd.AddValue("droneMaxHeight", "Maximum height of drones, m.", droneMaxHeight);
cmd.AddValue("areaSizeX", "X dimension of the simulation area, m.", areaSizeX);
cmd.AddValue("areaSizeY", "Y dimension of the simulation area, m.", areaSizeY);

cmd.Parse(argc, argv);
return true;
}

void
DroneWith5GExample::Run()
{
CreateNodes();
ConfigureMobility();
Install5GDevices();
InstallInternetStack();
InstallApplications();

std::cout << "Starting simulation for " << simTime << " s ...\n";

// Setup netsimulyzer for visualization
auto orchestrator = CreateObject<netsimulyzer::Orchestrator>("drone_5g_simulation.json");
netsimulyzer::NodeConfigurationHelper nodeHelper{orchestrator};
nodeHelper.Set("Model", netsimulyzer::models::QUADCOPTER_UAV_VALUE);

// Visualize drones
nodeHelper.Install(droneUEs);

// Use a different model for gNBs
nodeHelper.Set("Model", netsimulyzer::models::CELL_TOWER_VALUE);
nodeHelper.Install(gNbNodes);

Simulator::Stop(Seconds(simTime));
Simulator::Run();
Simulator::Destroy();
}

void
DroneWith5GExample::Report(std::ostream& os)
{
os << "Simulation completed with " << numDrones << " drones and "
<< gNbNodes.GetN() << " gNBs." << std::endl;
}

void
DroneWith5GExample::CreateNodes()
{
std::cout << "Creating " << numDrones << " drone UEs and 1 gNB." << std::endl;

// Create drone UEs
droneUEs.Create(numDrones);

// Create gNB node(s)
gNbNodes.Create(1);

// Name nodes
for (uint32_t i = 0; i < numDrones; ++i)
{
std::ostringstream os;
os << "drone-" << i;
Names::Add(os.str(), droneUEs.Get(i));
}

Names::Add("gNB-0", gNbNodes.Get(0));
}

void
DroneWith5GExample::ConfigureMobility()
{
// Set positions for gNBs (fixed)
MobilityHelper gNbMobility;
Ptr<ListPositionAllocator> gNbPositionAlloc = CreateObject<ListPositionAllocator>();

// Position the gNB in the center of the area at specified height
gNbPositionAlloc->Add(Vector(areaSizeX / 2.0, areaSizeY / 2.0, gNbHeight));
gNbMobility.SetPositionAllocator(gNbPositionAlloc);
gNbMobility.SetMobilityModel("ns3::ConstantPositionMobilityModel");
gNbMobility.Install(gNbNodes);

// Set mobility model for drones
MobilityHelper droneMobility;

// Initial positions of drones (random within the area)
Ptr<RandomBoxPositionAllocator> dronePositionAlloc = CreateObject<RandomBoxPositionAllocator>();
Ptr<UniformRandomVariable> xPos = CreateObject<UniformRandomVariable>();
xPos->SetAttribute("Min", DoubleValue(0.0));
xPos->SetAttribute("Max", DoubleValue(areaSizeX));
Ptr<UniformRandomVariable> yPos = CreateObject<UniformRandomVariable>();
yPos->SetAttribute("Min", DoubleValue(0.0));
yPos->SetAttribute("Max", DoubleValue(areaSizeY));
Ptr<UniformRandomVariable> zPos = CreateObject<UniformRandomVariable>();
zPos->SetAttribute("Min", DoubleValue(droneMinHeight));
zPos->SetAttribute("Max", DoubleValue(droneMaxHeight));

dronePositionAlloc->SetX(xPos);
dronePositionAlloc->SetY(yPos);
dronePositionAlloc->SetZ(zPos);
droneMobility.SetPositionAllocator(dronePositionAlloc);

// Gauss-Markov mobility model for drones
droneMobility.SetMobilityModel("ns3::GaussMarkovMobilityModel",
"Bounds", BoxValue(Box(0, areaSizeX, 0, areaSizeY, droneMinHeight, droneMaxHeight)),
"TimeStep", TimeValue(Seconds(0.1)),
"Alpha", DoubleValue(0.85),
"MeanVelocity", StringValue("ns3::UniformRandomVariable[Min=3|Max=10]"),
"MeanDirection", StringValue("ns3::UniformRandomVariable[Min=0|Max=6.283185307]"),
"MeanPitch", StringValue("ns3::UniformRandomVariable[Min=-0.2|Max=0.2]"),
"NormalVelocity", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=2.0|Bound=4.0]"),
"NormalDirection", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.2|Bound=0.4]"),
"NormalPitch", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.02|Bound=0.04]"));

droneMobility.Install(droneUEs);
}

void
DroneWith5GExample::Install5GDevices()
{
// Set up the 5G helper
Ptr<NrHelper> nrHelper = CreateObject<NrHelper>();
Ptr<NrPointToPointEpcHelper> epcHelper = CreateObject<NrPointToPointEpcHelper>();
nrHelper->SetEpcHelper(epcHelper);

// Configure bandwidth and frequency
BandwidthPartInfoPtrVector allBwps;
CcBwpCreator ccBwpCreator;

// Component carrier configuration
const uint8_t numCcPerBand = 1;  // Number of component carriers per band
CcBwpCreator::SimpleOperationBandConf bandConf(28e9, 100e6, numCcPerBand, BandwidthPartInfo::UMi_StreetCanyon);

// Configure both gNBs and UEs with the same configuration
OperationBandInfo band = ccBwpCreator.CreateOperationBandContiguousCc(bandConf);

// Configure the gNB device
nrHelper->SetGnbPhyAttribute("TxPower", DoubleValue(43.0)); // in dBm
nrHelper->SetGnbPhyAttribute("Numerology", UintegerValue(0));
nrHelper->SetGnbAntennaAttribute("NumRows", UintegerValue(4));
nrHelper->SetGnbAntennaAttribute("NumColumns", UintegerValue(4));

// Configure the UE device
nrHelper->SetUePhyAttribute("TxPower", DoubleValue(23.0)); // in dBm
nrHelper->SetUePhyAttribute("Numerology", UintegerValue(0));

// Configure the antenna for the UEs
nrHelper->SetUeAntennaAttribute("NumRows", UintegerValue(2));
nrHelper->SetUeAntennaAttribute("NumColumns", UintegerValue(2));

// Install the 5G devices
NetDeviceContainer enbNetDev = nrHelper->InstallGnbDevice(gNbNodes, band);
NetDeviceContainer ueNetDev = nrHelper->InstallUeDevice(droneUEs, band);

gNbDevices = enbNetDev;
ueDevices = ueNetDev;

// Attach UEs to the closest gNB
nrHelper->AttachToClosestEnb(ueNetDev, enbNetDev);

// Enable traces if pcap is true
if (pcap)
{
// Enable PCAP traces
nrHelper->EnableTraces();
}
}

void
DroneWith5GExample::InstallInternetStack()
{
// Install the Internet stack on the UEs
InternetStackHelper internet;
internet.Install(droneUEs);

// Assign IP addresses to UE devices
Ipv4AddressHelper ipv4h;
ipv4h.SetBase("10.0.0.0", "255.0.0.0");
ueIfaces = ipv4h.Assign(ueDevices);

// Get the default gateway address for routing
Ipv4StaticRoutingHelper ipv4RoutingHelper;
Ptr<Ipv4> ipv4 = droneUEs.Get(0)->GetObject<Ipv4>();
Ptr<Ipv4StaticRouting> staticRouting = ipv4RoutingHelper.GetStaticRouting(ipv4);
staticRouting->SetDefaultRoute(epcHelper->GetUeDefaultGatewayAddress(), 1);

if (printRoutes)
{
Ptr<OutputStreamWrapper> routingStream =
Create<OutputStreamWrapper>("drone_5g.routes", std::ios::out);
Ipv4RoutingHelper::PrintRoutingTableAllAt(Seconds(5), routingStream);
}
}

void
DroneWith5GExample::InstallApplications()
{
// Install ping application to test connectivity
// Let's ping from the first drone to the last drone
if (numDrones > 1)
{
uint32_t lastDroneIndex = numDrones - 1;
PingHelper ping(ueIfaces.GetAddress(lastDroneIndex));
ping.SetAttribute("VerboseMode", EnumValue(Ping::VerboseMode::VERBOSE));

ApplicationContainer pingApps = ping.Install(droneUEs.Get(0));
pingApps.Start(Seconds(1.0));
pingApps.Stop(Seconds(simTime - 1.0));
}

// Additional applications can be added here for testing data transmission
// For example, UDP client/server applications can be used to test throughput
}
Step3: Run Code
(Consider we are at /scratch directory)
Go to Terminal:
cd ..
./ns3 run scratch/test5g.cc












# Slicing Integration
# Setup Code
### Write Code
Step1: Go to /scratch directory
(Consider we are at /username directory)
Go to Terminal:
cd Desktop
cd project
cd project
cd ns-allinone-3.42
cd ns-3.42
cd scratch


Step2: Write code
(Consider we are at /scratch directory)
Go to Terminal:


(Paste the code provided below)
Press: Ctrl+x
Write: Y
Press: Enter

Code
#include "ns3/aodv-module.h"
#include "ns3/core-module.h"
#include "ns3/internet-module.h"
#include "ns3/mobility-module.h"
#include "ns3/network-module.h"
#include "ns3/ping-helper.h"
#include "ns3/point-to-point-module.h"
#include "ns3/applications-module.h"
#include "ns3/flow-monitor-module.h"
#include "ns3/nr-module.h"
#include "ns3/eps-bearer-tag.h"
#include "ns3/lte-module.h"
#include <ns3/netsimulyzer-module.h>
#include <cmath>
#include <iostream>
#include <map>
#include <string>

using namespace ns3;

/**
* @brief Drone simulation with 5G network slicing.
*
* This script creates a 5G network with drones as UEs (User Equipment)
* and a gNB (5G base station) with network slicing capabilities.
*
* Three network slices are implemented:
* 1. eMBB (enhanced Mobile Broadband) - for high data rate applications
* 2. URLLC (Ultra-Reliable Low-Latency Communications) - for critical control
* 3. mMTC (massive Machine Type Communications) - for telemetry data
*/
class DroneNetworkSlicingExample
{
public:
DroneNetworkSlicingExample();
bool Configure(int argc, char** argv);
void Run();
void Report(std::ostream& os);

private:
// Slice types
enum SliceType {
EMBB,   // Enhanced Mobile Broadband
URLLC,  // Ultra-Reliable Low-Latency Communications
MMTC	// Massive Machine Type Communications
};

// parameters
uint32_t numDrones;      	// Number of drone UEs
double simTime;          	// Simulation time in seconds
bool pcap;               	// Write PCAP traces if true
bool printRoutes;        	// Print routing tables if true
double gNbHeight;        	// Height of the gNB in meters
double droneMinHeight;   	// Minimum height of drones in meters
double droneMaxHeight;   	// Maximum height of drones in meters
double areaSizeX;        	// X dimension of the simulation area
double areaSizeY;        	// Y dimension of the simulation area

// Slicing parameters
uint32_t numEmbbDrones;  	// Number of drones in eMBB slice
uint32_t numUrllcDrones; 	// Number of drones in URLLC slice
uint32_t numMmtcDrones;  	// Number of drones in mMTC slice

// network
NodeContainer droneUEs;       	// All drone nodes acting as UEs
NodeContainer gNbNodes;       	// gNB nodes (base stations)
NodeContainer embbDrones;     	// Drones in eMBB slice
NodeContainer urllcDrones;    	// Drones in URLLC slice
NodeContainer mmtcDrones;     	// Drones in mMTC slice

NetDeviceContainer ueDevices; 	// All UE devices
NetDeviceContainer gNbDevices;	// gNB devices
NetDeviceContainer embbDevices;   // eMBB slice devices
NetDeviceContainer urllcDevices;  // URLLC slice devices
NetDeviceContainer mmtcDevices;   // mMTC slice devices

Ipv4InterfaceContainer ueIfaces;  // UE interfaces
Ipv4InterfaceContainer gNbIfaces; // gNB interfaces

// Map to keep track of which drones belong to which slice
std::map<uint32_t, SliceType> droneSliceMap;

// EPC helper for accessing core network
Ptr<NrPointToPointEpcHelper> epcHelper;

// Flow monitor for traffic analysis
Ptr<FlowMonitor> flowMonitor;
FlowMonitorHelper flowHelper;

private:
void CreateNodes();
void ConfigureMobility();
void Install5GDevices();
void InstallInternetStack();
void ConfigureNetworkSlices();
void InstallApplications();
void InstallEmbbApplications();
void InstallUrllcApplications();
void InstallMmtcApplications();
EpsBearer CreateBearerForSlice(SliceType slice);
};

int
main(int argc, char** argv)
{
DroneNetworkSlicingExample test;
if (!test.Configure(argc, argv))
{
NS_FATAL_ERROR("Configuration failed. Aborted.");
}

test.Run();
test.Report(std::cout);
return 0;
}

//-----------------------------------------------------------------------------
DroneNetworkSlicingExample::DroneNetworkSlicingExample()
: numDrones(30),
simTime(100),
pcap(true),
printRoutes(true),
gNbHeight(30.0),
droneMinHeight(10.0),
droneMaxHeight(50.0),
areaSizeX(500.0),
areaSizeY(500.0),
numEmbbDrones(10),
numUrllcDrones(10),
numMmtcDrones(10)
{
}

bool
DroneNetworkSlicingExample::Configure(int argc, char** argv)
{
SeedManager::SetSeed(12345);
CommandLine cmd(FILE);

cmd.AddValue("pcap", "Write PCAP traces.", pcap);
cmd.AddValue("printRoutes", "Print routing table dumps.", printRoutes);
cmd.AddValue("numDrones", "Number of drone UEs.", numDrones);
cmd.AddValue("numEmbbDrones", "Number of drones in eMBB slice.", numEmbbDrones);
cmd.AddValue("numUrllcDrones", "Number of drones in URLLC slice.", numUrllcDrones);
cmd.AddValue("numMmtcDrones", "Number of drones in mMTC slice.", numMmtcDrones);
cmd.AddValue("simTime", "Simulation time, s.", simTime);
cmd.AddValue("gNbHeight", "Height of gNB, m.", gNbHeight);
cmd.AddValue("droneMinHeight", "Minimum height of drones, m.", droneMinHeight);
cmd.AddValue("droneMaxHeight", "Maximum height of drones, m.", droneMaxHeight);
cmd.AddValue("areaSizeX", "X dimension of the simulation area, m.", areaSizeX);
cmd.AddValue("areaSizeY", "Y dimension of the simulation area, m.", areaSizeY);

cmd.Parse(argc, argv);

// Ensure the total number of drones matches the sum of drones in each slice
if (numEmbbDrones + numUrllcDrones + numMmtcDrones != numDrones)
{
std::cerr << "ERROR: The sum of drones in all slices must equal numDrones!" << std::endl;
std::cerr << "numEmbbDrones + numUrllcDrones + numMmtcDrones = "
<< numEmbbDrones + numUrllcDrones + numMmtcDrones << std::endl;
std::cerr << "numDrones = " << numDrones << std::endl;
return false;
}

return true;
}

void
DroneNetworkSlicingExample::Run()
{
CreateNodes();
ConfigureMobility();
Install5GDevices();
InstallInternetStack();
ConfigureNetworkSlices();
InstallApplications();

std::cout << "Starting simulation for " << simTime << " s with "
<< numDrones << " drones in 3 network slices..." << std::endl;

// Setup netsimulyzer for visualization
auto orchestrator = CreateObject<netsimulyzer::Orchestrator>("drone_network_slicing.json");
netsimulyzer::NodeConfigurationHelper nodeHelper{orchestrator};

// Configure visualization for eMBB drones (red)
nodeHelper.Set("Model", netsimulyzer::models::QUADCOPTER_UAV_VALUE);
nodeHelper.Set("Color", Vector(1.0, 0.0, 0.0)); // Red for eMBB
nodeHelper.Install(embbDrones);

// Configure visualization for URLLC drones (blue)
nodeHelper.Set("Color", Vector(0.0, 0.0, 1.0)); // Blue for URLLC
nodeHelper.Install(urllcDrones);

// Configure visualization for mMTC drones (green)
nodeHelper.Set("Color", Vector(0.0, 1.0, 0.0)); // Green for mMTC
nodeHelper.Install(mmtcDrones);

// Configure visualization for gNBs
nodeHelper.Set("Model", netsimulyzer::models::CELL_TOWER_VALUE);
nodeHelper.Set("Color", Vector(0.5, 0.5, 0.5)); // Gray for gNBs
nodeHelper.Install(gNbNodes);

// Enable flow monitoring
flowMonitor = flowHelper.InstallAll();

// Schedule flow monitor output
Simulator::Schedule(Seconds(simTime - 1.0),
&DroneNetworkSlicingExample::Report,
this,
std::ref(std::cout));

Simulator::Stop(Seconds(simTime));
Simulator::Run();
Simulator::Destroy();
}

void
DroneNetworkSlicingExample::Report(std::ostream& os)
{
os << "\n--- Network Slicing Performance Report ---\n";

// Print flow monitor statistics
flowMonitor->CheckForLostPackets();
Ptr<Ipv4FlowClassifier> classifier = DynamicCast<Ipv4FlowClassifier>(flowHelper.GetClassifier());
std::map<FlowId, FlowMonitor::FlowStats> stats = flowMonitor->GetFlowStats();

os << "Flow\tSlice\tSrc\tDst\tTx Packets\tRx Packets\tLost\tDelay (ms)\tJitter (ms)\tThroughput (Mbps)\n";

double totalEmbbThroughput = 0.0;
double totalUrllcThroughput = 0.0;
double totalMmtcThroughput = 0.0;

double avgEmbbDelay = 0.0;
double avgUrllcDelay = 0.0;
double avgMmtcDelay = 0.0;

int embbFlowCount = 0;
int urllcFlowCount = 0;
int mmtcFlowCount = 0;

for (std::map<FlowId, FlowMonitor::FlowStats>::const_iterator i = stats.begin(); i != stats.end(); ++i)
{
Ipv4FlowClassifier::FiveTuple t = classifier->FindFlow(i->first);

// Skip flows that don't have received packets
if (i->second.rxPackets == 0)
continue;

// Calculate metrics
double throughput = i->second.rxBytes * 8.0 / (i->second.timeLastRxPacket.GetSeconds() - i->second.timeFirstTxPacket.GetSeconds()) / 1000000.0;
double delay = i->second.delaySum.GetMilliSeconds() / i->second.rxPackets;
double jitter = i->second.jitterSum.GetMilliSeconds() / i->second.rxPackets;

// Determine which slice this flow belongs to by checking the source IP
std::string sliceName;
uint32_t nodeId = t.sourceAddress.Get() & 0xFF; // Extract node ID from IP

if (droneSliceMap.find(nodeId) != droneSliceMap.end())
{
SliceType sliceType = droneSliceMap[nodeId];

switch (sliceType)
{
case EMBB:
sliceName = "eMBB";
totalEmbbThroughput += throughput;
avgEmbbDelay += delay;
embbFlowCount++;
break;
case URLLC:
sliceName = "URLLC";
totalUrllcThroughput += throughput;
avgUrllcDelay += delay;
urllcFlowCount++;
break;
case MMTC:
sliceName = "mMTC";
totalMmtcThroughput += throughput;
avgMmtcDelay += delay;
mmtcFlowCount++;
break;
default:
sliceName = "Unknown";
break;
}
}
else
{
sliceName = "Unknown";
}

os << i->first << "\t"
<< sliceName << "\t"
<< t.sourceAddress << "\t"
<< t.destinationAddress << "\t"
<< i->second.txPackets << "\t"
<< i->second.rxPackets << "\t"
<< i->second.lostPackets << "\t"
<< delay << "\t"
<< jitter << "\t"
<< throughput << "\n";
}

// Calculate and print average metrics per slice
os << "\n--- Average Metrics Per Slice ---\n";

if (embbFlowCount > 0)
{
avgEmbbDelay /= embbFlowCount;
os << "eMBB: Throughput = " << totalEmbbThroughput << " Mbps, Avg Delay = " << avgEmbbDelay << " ms\n";
}

if (urllcFlowCount > 0)
{
avgUrllcDelay /= urllcFlowCount;
os << "URLLC: Throughput = " << totalUrllcThroughput << " Mbps, Avg Delay = " << avgUrllcDelay << " ms\n";
}

if (mmtcFlowCount > 0)
{
avgMmtcDelay /= mmtcFlowCount;
os << "mMTC: Throughput = " << totalMmtcThroughput << " Mbps, Avg Delay = " << avgMmtcDelay << " ms\n";
}

os << "-----------------------------------\n";
}

void
DroneNetworkSlicingExample::CreateNodes()
{
std::cout << "Creating " << numDrones << " drone UEs and 1 gNB." << std::endl;

// Create drone UEs
droneUEs.Create(numDrones);

// Create gNB node(s)
gNbNodes.Create(1);

// Assign drones to slices
uint32_t currentIndex = 0;

// eMBB slice
for (uint32_t i = 0; i < numEmbbDrones; ++i, ++currentIndex)
{
embbDrones.Add(droneUEs.Get(currentIndex));
droneSliceMap[currentIndex] = EMBB;

std::ostringstream os;
os << "embb-drone-" << i;
Names::Add(os.str(), droneUEs.Get(currentIndex));
}

// URLLC slice
for (uint32_t i = 0; i < numUrllcDrones; ++i, ++currentIndex)
{
urllcDrones.Add(droneUEs.Get(currentIndex));
droneSliceMap[currentIndex] = URLLC;

std::ostringstream os;
os << "urllc-drone-" << i;
Names::Add(os.str(), droneUEs.Get(currentIndex));
}

// mMTC slice
for (uint32_t i = 0; i < numMmtcDrones; ++i, ++currentIndex)
{
mmtcDrones.Add(droneUEs.Get(currentIndex));
droneSliceMap[currentIndex] = MMTC;

std::ostringstream os;
os << "mmtc-drone-" << i;
Names::Add(os.str(), droneUEs.Get(currentIndex));
}

Names::Add("gNB-0", gNbNodes.Get(0));
}

void
DroneNetworkSlicingExample::ConfigureMobility()
{
// Set positions for gNBs (fixed)
MobilityHelper gNbMobility;
Ptr<ListPositionAllocator> gNbPositionAlloc = CreateObject<ListPositionAllocator>();

// Position the gNB in the center of the area at specified height
gNbPositionAlloc->Add(Vector(areaSizeX / 2.0, areaSizeY / 2.0, gNbHeight));
gNbMobility.SetPositionAllocator(gNbPositionAlloc);
gNbMobility.SetMobilityModel("ns3::ConstantPositionMobilityModel");
gNbMobility.Install(gNbNodes);

// Set mobility model for drones - use different mobility patterns for each slice

// 1. eMBB drones - higher altitude, wider area coverage
MobilityHelper embbMobility;
Ptr<RandomBoxPositionAllocator> embbPositionAlloc = CreateObject<RandomBoxPositionAllocator>();
Ptr<UniformRandomVariable> embbXPos = CreateObject<UniformRandomVariable>();
embbXPos->SetAttribute("Min", DoubleValue(0.0));
embbXPos->SetAttribute("Max", DoubleValue(areaSizeX));
Ptr<UniformRandomVariable> embbYPos = CreateObject<UniformRandomVariable>();
embbYPos->SetAttribute("Min", DoubleValue(0.0));
embbYPos->SetAttribute("Max", DoubleValue(areaSizeY));
Ptr<UniformRandomVariable> embbZPos = CreateObject<UniformRandomVariable>();
embbZPos->SetAttribute("Min", DoubleValue(droneMaxHeight * 0.7));
embbZPos->SetAttribute("Max", DoubleValue(droneMaxHeight));

embbPositionAlloc->SetX(embbXPos);
embbPositionAlloc->SetY(embbYPos);
embbPositionAlloc->SetZ(embbZPos);
embbMobility.SetPositionAllocator(embbPositionAlloc);

embbMobility.SetMobilityModel("ns3::GaussMarkovMobilityModel",
"Bounds", BoxValue(Box(0, areaSizeX, 0, areaSizeY, droneMaxHeight * 0.7, droneMaxHeight)),
"TimeStep", TimeValue(Seconds(0.5)),
"Alpha", DoubleValue(0.85),
"MeanVelocity", StringValue("ns3::UniformRandomVariable[Min=5|Max=15]"),
"MeanDirection", StringValue("ns3::UniformRandomVariable[Min=0|Max=6.283185307]"),
"MeanPitch", StringValue("ns3::UniformRandomVariable[Min=-0.1|Max=0.1]"),
"NormalVelocity", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=2.0|Bound=4.0]"),
"NormalDirection", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.2|Bound=0.4]"),
"NormalPitch", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.02|Bound=0.04]"));

embbMobility.Install(embbDrones);

// 2. URLLC drones - medium altitude, faster movement for critical missions
MobilityHelper urllcMobility;
Ptr<RandomBoxPositionAllocator> urllcPositionAlloc = CreateObject<RandomBoxPositionAllocator>();
Ptr<UniformRandomVariable> urllcXPos = CreateObject<UniformRandomVariable>();
urllcXPos->SetAttribute("Min", DoubleValue(areaSizeX * 0.2));
urllcXPos->SetAttribute("Max", DoubleValue(areaSizeX * 0.8));
Ptr<UniformRandomVariable> urllcYPos = CreateObject<UniformRandomVariable>();
urllcYPos->SetAttribute("Min", DoubleValue(areaSizeY * 0.2));
urllcYPos->SetAttribute("Max", DoubleValue(areaSizeY * 0.8));
Ptr<UniformRandomVariable> urllcZPos = CreateObject<UniformRandomVariable>();
urllcZPos->SetAttribute("Min", DoubleValue((droneMinHeight + droneMaxHeight) * 0.4));
urllcZPos->SetAttribute("Max", DoubleValue((droneMinHeight + droneMaxHeight) * 0.6));

urllcPositionAlloc->SetX(urllcXPos);
urllcPositionAlloc->SetY(urllcYPos);
urllcPositionAlloc->SetZ(urllcZPos);
urllcMobility.SetPositionAllocator(urllcPositionAlloc);

urllcMobility.SetMobilityModel("ns3::GaussMarkovMobilityModel",
"Bounds", BoxValue(Box(0, areaSizeX, 0, areaSizeY, droneMinHeight, droneMaxHeight)),
"TimeStep", TimeValue(Seconds(0.1)),
"Alpha", DoubleValue(0.75),
"MeanVelocity", StringValue("ns3::UniformRandomVariable[Min=10|Max=20]"),
"MeanDirection", StringValue("ns3::UniformRandomVariable[Min=0|Max=6.283185307]"),
"MeanPitch", StringValue("ns3::UniformRandomVariable[Min=-0.2|Max=0.2]"),
"NormalVelocity", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=3.0|Bound=6.0]"),
"NormalDirection", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.3|Bound=0.6]"),
"NormalPitch", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.03|Bound=0.06]"));

urllcMobility.Install(urllcDrones);

// 3. mMTC drones - lower altitude, slower movement for sensor data collection
MobilityHelper mmtcMobility;
Ptr<RandomBoxPositionAllocator> mmtcPositionAlloc = CreateObject<RandomBoxPositionAllocator>();
Ptr<UniformRandomVariable> mmtcXPos = CreateObject<UniformRandomVariable>();
mmtcXPos->SetAttribute("Min", DoubleValue(0.0));
mmtcXPos->SetAttribute("Max", DoubleValue(areaSizeX));
Ptr<UniformRandomVariable> mmtcYPos = CreateObject<UniformRandomVariable>();
mmtcYPos->SetAttribute("Min", DoubleValue(0.0));
mmtcYPos->SetAttribute("Max", DoubleValue(areaSizeY));
Ptr<UniformRandomVariable> mmtcZPos = CreateObject<UniformRandomVariable>();
mmtcZPos->SetAttribute("Min", DoubleValue(droneMinHeight));
mmtcZPos->SetAttribute("Max", DoubleValue(droneMinHeight * 1.5));

mmtcPositionAlloc->SetX(mmtcXPos);
mmtcPositionAlloc->SetY(mmtcYPos);
mmtcPositionAlloc->SetZ(mmtcZPos);
mmtcMobility.SetPositionAllocator(mmtcPositionAlloc);

mmtcMobility.SetMobilityModel("ns3::GaussMarkovMobilityModel",
"Bounds", BoxValue(Box(0, areaSizeX, 0, areaSizeY, droneMinHeight, droneMinHeight * 1.5)),
"TimeStep", TimeValue(Seconds(1.0)),
"Alpha", DoubleValue(0.95),
"MeanVelocity", StringValue("ns3::UniformRandomVariable[Min=1|Max=5]"),
"MeanDirection", StringValue("ns3::UniformRandomVariable[Min=0|Max=6.283185307]"),
"MeanPitch", StringValue("ns3::UniformRandomVariable[Min=-0.05|Max=0.05]"),
"NormalVelocity", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=1.0|Bound=2.0]"),
"NormalDirection", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.1|Bound=0.2]"),
"NormalPitch", StringValue("ns3::NormalRandomVariable[Mean=0.0|Variance=0.01|Bound=0.02]"));

mmtcMobility.Install(mmtcDrones);
}

void
DroneNetworkSlicingExample::Install5GDevices()
{
// Set up the 5G helper
Ptr<NrHelper> nrHelper = CreateObject<NrHelper>();
epcHelper = CreateObject<NrPointToPointEpcHelper>();
nrHelper->SetEpcHelper(epcHelper);

// Configure bandwidth and frequency
BandwidthPartInfoPtrVector allBwps;
CcBwpCreator ccBwpCreator;

// Component carrier configuration
const uint8_t numCcPerBand = 1;  // Number of component carriers per band
// For 5G NR FR2 band n257 (28 GHz)
CcBwpCreator::SimpleOperationBandConf bandConf(28e9, 100e6, numCcPerBand, BandwidthPartInfo::UMi_StreetCanyon);

// Configure both gNBs and UEs with the same configuration
OperationBandInfo band = ccBwpCreator.CreateOperationBandContiguousCc(bandConf);

// Configure the gNB device
nrHelper->SetGnbPhyAttribute("TxPower", DoubleValue(46.0)); // in dBm
nrHelper->SetGnbPhyAttribute("Numerology", UintegerValue(2)); // Numerology 2 (60 kHz SCS)
nrHelper->SetGnbAntennaAttribute("NumRows", UintegerValue(8));
nrHelper->SetGnbAntennaAttribute("NumColumns", UintegerValue(8));
nrHelper->SetGnbAntennaAttribute("AntennaElement", StringValue("IsotropicAntennaModel"));

// Configure the UE device
nrHelper->SetUePhyAttribute("TxPower", DoubleValue(23.0)); // in dBm
nrHelper->SetUePhyAttribute("Numerology", UintegerValue(2)); // Numerology 2 (60 kHz SCS)

// Configure the antenna for the UEs
nrHelper->SetUeAntennaAttribute("NumRows", UintegerValue(2));
nrHelper->SetUeAntennaAttribute("NumColumns", UintegerValue(2));
nrHelper->SetUeAntennaAttribute("AntennaElement", StringValue("IsotropicAntennaModel"));

// Install the 5G devices
NetDeviceContainer enbNetDev = nrHelper->InstallGnbDevice(gNbNodes, band);
NetDeviceContainer ueNetDev = nrHelper->InstallUeDevice(droneUEs, band);

gNbDevices = enbNetDev;
ueDevices = ueNetDev;

// Separate devices by slice for easier management
for (uint32_t i = 0; i < numDrones; i++)
{
Ptr<NetDevice> device = ueNetDev.Get(i);

if (droneSliceMap.find(i) != droneSliceMap.end())
{
SliceType sliceType = droneSliceMap[i];

switch (sliceType)
{
case EMBB:
embbDevices.Add(device);
break;
case URLLC:
urllcDevices.Add(device);
break;
case MMTC:
mmtcDevices.Add(device);
break;
}
}
}

// Attach UEs to the closest gNB
nrHelper->AttachToClosestEnb(ueNetDev, enbNetDev);

// Enable traces if pcap is true
if (pcap)
{
// Enable PCAP traces
nrHelper->EnableTraces();
}
}

void
DroneNetworkSlicingExample::InstallInternetStack()
{
// Install the Internet stack on the UEs
InternetStackHelper internet;
internet.Install(droneUEs);

// Assign IP addresses to UE devices
Ipv4AddressHelper ipv4h;
ipv4h.SetBase("10.0.0.0", "255.0.0.0");
ueIfaces = ipv4h.Assign(ueDevices);

// Get the default gateway address for routing
Ipv4StaticRoutingHelper ipv4RoutingHelper;
for (uint32_t i = 0; i < droneUEs.GetN(); i++)
{
Ptr<Ipv4> ipv4 = droneUEs.Get(i)->GetObject<Ipv4>();
Ptr<Ipv4StaticRouting> staticRouting = ipv4RoutingHelper.GetStaticRouting(ipv4);
staticRouting->SetDefaultRoute(epcHelper->GetUeDefaultGatewayAddress(), 1);
}

if (printRoutes)
{
Ptr<OutputStreamWrapper> routingStream =
Create<OutputStreamWrapper>("drone_network_slicing.routes", std::ios::out);
Ipv4RoutingHelper::PrintRoutingTableAllAt(Seconds(5), routingStream);
}
}

EpsBearer
DroneNetworkSlicingExample::CreateBearerForSlice(SliceType slice)
{
EpsBearer::Qci qci;
GbrQosInformation qosInfo;
bool isGbr = false;

switch (slice)
{
case EMBB:
// Enhanced Mobile Broadband - high throughput, moderate latency
qci = EpsBearer::GBR_CONV_VIDEO;  // Video streaming
qosInfo.gbrDl = 10000000;     	// 10 Mbps DL GBR
qosInfo.gbrUl = 5000000;      	// 5 Mbps UL GBR
qosInfo.mbrDl = 100000000;    	// 100 Mbps DL MBR
qosInfo.mbrUl = 50000000;     	// 50 Mbps UL MBR
isGbr = true;
break;

case URLLC:
// Ultra-Reliable Low-Latency - low latency, high reliability
qci = EpsBearer::GBR_MC_PUSH_TO_TALK;	// Mission critical PTT voice
qosInfo.gbrDl = 1000000;             	// 1 Mbps DL GBR
qosInfo.gbrUl = 1000000;             	// 1 Mbps UL GBR
qosInfo.mbrDl = 10000000;            	// 10 Mbps DL MBR
qosInfo.mbrUl = 10000000;            	// 10 Mbps UL MBR
isGbr = true;
break;

case MMTC:
// Massive Machine Type Communications - many devices, low data rates
qci = EpsBearer::NGBR_IOT;           	// Non-GBR IoT data
isGbr = false;
break;

default:
// Default bearer
qci = EpsBearer::NGBR_VIDEO_TCP_DEFAULT;
isGbr = false;
break;
}

if (isGbr)
{
return EpsBearer(qci, qosInfo);
}
else
{
return EpsBearer(qci);
}
}

void
DroneNetworkSlicingExample::ConfigureNetworkSlices()
{
std::cout << "Configuring network slices..." << std::endl;

// Get the EPC PGW (Packet Gateway)
Ptr<Node> pgw = epcHelper->GetPgwNode();

// For each UE, create a dedicated bearer based on its slice
for (uint32_t i = 0; i < numDrones; i++)
{
if (droneSliceMap.find(i) != droneSliceMap.end())
{
SliceType sliceType = droneSliceMap[i];
EpsBearer bearer = CreateBearerForSlice(sliceType);

// Create dedicated bearer for the UE
Ptr<NetDevice> ueDevice = ueDevices.Get(i);
Ptr<NetDevice> enbDevice = gNbDevices.Get(0); // Assuming single gNB

// Activate bearer
nrHelper->ActivateDedicatedEpsBearer(ueDevice, bearer, EpcTft::Default());
}
}
}

void
DroneNetworkSlicingExample::InstallApplications()
{
// Install applications for each slice type
InstallEmbbApplications();
InstallUrllcApplications();
InstallMmtcApplications();
}

void
DroneNetworkSlicingExample::InstallEmbbApplications()
{
// For eMBB slice, we'll set up high-throughput applications (video streaming)
// Remote host for server applications
Ptr<Node> remoteHost = epcHelper->GetPgwNode();

// Install UDP server on remote host
uint16_t dlPort = 1000;
ApplicationContainer serverApps;

// Setup high-bandwidth UDP server for video streaming
for (uint32_t i = 0; i < embbDrones.GetN(); i++)
{
// Video streaming server (downlink)
UdpServerHelper dlServer(dlPort + i);
serverApps.Add(dlServer.Install(remoteHost));

// Video streaming client on drone (downlink)
UdpClientHelper dlClient(epcHelper->GetUeDefaultGatewayAddress(), dlPort + i);
dlClient.SetAttribute("MaxPackets", UintegerValue(1000000));
dlClient.SetAttribute("Interval", TimeValue(Seconds(0.01)));  // 100 pkts/sec
dlClient.SetAttribute("PacketSize", UintegerValue(1400)); 	// 1400 bytes

ApplicationContainer clientApps = dlClient.Install(embbDrones.Get(i));
clientApps.Start(Seconds(1.0));
clientApps.Stop(Seconds(simTime - 1.0));
}

serverApps.Start(Seconds(0.5));
serverApps.Stop(Seconds(simTime - 0.5));
}

void
DroneNetworkSlicingExample::InstallUrllcApplications()
{
// For URLLC slice, we'll set up low-latency applications (drone control)
// Remote host for server applications
Ptr<Node> remoteHost = epcHelper->GetPgwNode();

// Install UDP server on remote host
uint16_t dlPort = 2000;
uint16_t ulPort = 3000;
ApplicationContainer serverApps;

// Setup low-latency UDP applications for drone control
for (uint32_t i = 0; i < urllcDrones.GetN(); i++)
{
// Control command server (downlink)
UdpServerHelper dlServer(dlPort + i);
serverApps.Add(dlServer.Install(remoteHost));

// Telemetry server (uplink)
UdpServerHelper ulServer(ulPort + i);
serverApps.Add(ulServer.Install(remoteHost));

// Control command client on drone (downlink)
UdpClientHelper dlClient(epcHelper->GetUeDefaultGatewayAddress(), dlPort + i);
dlClient.SetAttribute("MaxPackets", UintegerValue(1000000));
dlClient.SetAttribute("Interval", TimeValue(Seconds(0.005)));  // 200 pkts/sec
dlClient.SetAttribute("PacketSize", UintegerValue(64));    	// Small packets

// Telemetry client on drone (uplink)
UdpClientHelper ulClient(epcHelper->GetUeDefaultGatewayAddress(), ulPort + i);
ulClient.SetAttribute("MaxPackets", UintegerValue(1000000));
ulClient.SetAttribute("Interval", TimeValue(Seconds(0.005)));  // 200 pkts/sec
ulClient.SetAttribute("PacketSize", UintegerValue(64));    	// Small packets

ApplicationContainer clientDlApps = dlClient.Install(urllcDrones.Get(i));
ApplicationContainer clientUlApps = ulClient.Install(urllcDrones.Get(i));

clientDlApps.Start(Seconds(1.0));
clientDlApps.Stop(Seconds(simTime - 1.0));

clientUlApps.Start(Seconds(1.1));
clientUlApps.Stop(Seconds(simTime - 0.9));
}

serverApps.Start(Seconds(0.5));
serverApps.Stop(Seconds(simTime - 0.5));
}

void
DroneNetworkSlicingExample::InstallMmtcApplications()
{
// For mMTC slice, we'll set up many small, infrequent transmissions (sensor data)
// Remote host for server applications
Ptr<Node> remoteHost = epcHelper->GetPgwNode();

// Install UDP server on remote host
uint16_t sensorPort = 4000;
ApplicationContainer serverApps;

// Setup sensor data transmission (many small packets, infrequent)
for (uint32_t i = 0; i < mmtcDrones.GetN(); i++)
{
// Sensor data collection server
UdpServerHelper sensorServer(sensorPort + i);
serverApps.Add(sensorServer.Install(remoteHost));

// Sensor data client on drone
UdpClientHelper sensorClient(epcHelper->GetUeDefaultGatewayAddress(), sensorPort + i);
sensorClient.SetAttribute("MaxPackets", UintegerValue(1000000));

// Random interval between 1-5 seconds to simulate diverse IoT patterns
Ptr<UniformRandomVariable> interval = CreateObject<UniformRandomVariable>();
interval->SetAttribute("Min", DoubleValue(1.0));
interval->SetAttribute("Max", DoubleValue(5.0));

// Set interval for sensor data
double sendInterval = interval->GetValue();
sensorClient.SetAttribute("Interval", TimeValue(Seconds(sendInterval)));
sensorClient.SetAttribute("PacketSize", UintegerValue(100));  // Small sensor readings

ApplicationContainer clientApps = sensorClient.Install(mmtcDrones.Get(i));
clientApps.Start(Seconds(1.0 + i * 0.1)); // Stagger start times
clientApps.Stop(Seconds(simTime - 1.0));
}

serverApps.Start(Seconds(0.5));
serverApps.Stop(Seconds(simTime - 0.5));
}


Step3: Run Code
(Consider we are at /scratch directory)
Go to Terminal:
cd ..
./ns3 run scratch/test_slicing.cc


# Running Simulation
# All Simulations
Wifi


5g nr

Sliced

Thank You
