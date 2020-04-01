# using python to make a xml file in some certain format 

import xml.dom.minidom

#build a new xml file
doc = xml.dom.minidom.Document() 
#creat a root node named 'Mangers'
root = doc.createElement('Managers') 
#set node attributes 
root.setAttribute('company', 'ASD') 
root.setAttribute('address', 'Shanghai') 
#add root node to the file
doc.appendChild(root) 

managerList = [{'name' : 'joy',  'age' : 27, 'gender' : 'F'},
               {'name' : 'tom', 'age' : 30, 'gender' : 'M'},
               {'name' : 'ruby', 'age' : 29, 'gender' : 'F'}
]

for i in managerList :
  nodeManager = doc.createElement('Manager')
  nodeName = doc.createElement('name')
  #add text for a child node
  nodeName.appendChild(doc.createTextNode(str(i['name'])))

  nodeAge = doc.createElement("age")
  nodeAge.appendChild(doc.createTextNode(str(i["age"])))

  nodeSex = doc.createElement("sex")
  nodeSex.appendChild(doc.createTextNode(str(i["sex"])))

  #add all child nodes into root node
  nodeManager.appendChild(nodeName)
  nodeManager.appendChild(nodeAge)
  nodeManager.appendChild(nodeSex)
  root.appendChild(nodeManager)
  
#output
fp = open('c:\\wcx\\Manager.xml', 'w')
doc.writexml(fp, indent='\t', addindent='\t', newl='\n', encoding="utf-8")
