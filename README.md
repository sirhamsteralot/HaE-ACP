# HaE-ACP
Feature rich Antenna Protocol wrapper for SE.
the base communications protocol i use is:
`entityid(sender)|entityid(receiver)?Parameter1|Parameter2|Parameter3|etc.` format


## How to use:
- grab code from source.cs and paste it in your project somehow.


## Code:
here is where i discribe all the usefull info :)

### Constructors:
- public ACPWrapper(Program p, Func<IMyTerminalBlock, bool> collect = null)
  Initializes an instance of ACPWrapper with a list of Radio antennas.
  
- public ACPWrapper(Program p, bool HasList, List<IMyRadioAntenna> list = null)
  Initializes an instance of ACPWrapper with a list of Radio antennas.
  
- public ACPWrapper(Program p, IMyLaserAntenna lAntenna)
  Initializes an instance of ACPWrapper with a single laser antenna (will require additional setup, see further down under SetLaserTarget tho you can also manually connect through GUI).
  
- public ACPWrapper(Program p, IMyRadioAntenna antenna)
  Initializes an instance of ACPWrapper with a single radio antenna.
  
- public ACPWrapper(Program p, string antennaName)
  Initializes an instance of ACPWrapper with either a radio  or laser antenna depending on what it finds with the name.
  
### Public Methods:

#### AddAdress(long Id, string Name)
  Adds a new adress to the adressbook with specified ID and Name.
  
#### PrepareMSG (overloaded)
##### PrepareMSG(string[] parameters, long To, bool anon = false)
  Puts a message in the queue to be send the next time the PB is run/ it is its time in the queue (only one msg/tick/antenna)
  The parameters is actually what gets send and what will be returned by Main() when a PB receives a msg, To is the entity ID of the recipiant

##### public bool PrepareMSG(string[] parameters, string To, bool anon = false)
  Puts a message in the queue to be send the next time the PB is run/ it is its time in the queue (only one msg/tick/antenna)
  The parameters is actually what gets send and what will be returned by Main() when a PB receives a msg, To is the entity ID of the recipiant
  
#### Ping()
  Sends out a ping message so that other PBS can add the one you are on to their adressbook.
  
#### Pong()
  Basically the same as Ping but this will also send your own entityID and this will also not trigger other PBs to "Pong" back.
  
#### public void SetLaserTarget(Vector3D location)
  Sets a target for the laser antenna (if present) using a vector3D
  
#### public void SetLaserTarget(string GPS)
  Sets a target for the laser antenna (if present) using a GPS waypoint string `GPS:Name:X:Y:Z:` Format
  
#### public long? GetIdWithName(string Name)
  Returns first ID with `Name` in the adressBook.
