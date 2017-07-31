# My-Repository
My code

I'm just trying the app for the first time.

        /// <summary>
        /// TreeView Populate.
        /// </summary>
        /// <param name="lastNode">Last node added</param>
        /// <param name="newNode">New node to add</param>
        private void TreViewPopulate(TreeNode lastNode, TreeNode newNode)
        {
            int currentlevel = ((KeyValuePair<int, DoorLocationServerState>)newNode.Tag).Key; 
            int lastLevel = ((KeyValuePair<int, DoorLocationServerState>)lastNode.Tag).Key; 

            if (currentlevel < lastLevel)
            {
                if (currentlevel == 1)
                    tvDoorRelations.Nodes.Add(newNode);
                else
                {
                    TreeNode currentNode = lastNode.Parent;
                    for (int j = 0; j < lastLevel - (currentlevel + 1); j++)
                        currentNode = currentNode.Parent;
                    currentNode.Nodes.Add(newNode);
                }
            }
            else if (currentlevel == lastLevel)
            {
                if (lastLevel == 1)
                    tvDoorRelations.Nodes.Add(newNode);
                else
                    lastNode.Parent.Nodes.Add(newNode);
            }
            else
                lastNode.Nodes.Add(newNode);
        }
