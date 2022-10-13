# Deep_Learning_JupyterLab
This is to spin up a JupyterLab in Kubnetes to use the DL models trained and shipped from Google Colab.
<p>
  1.  Create a host volume on K8s nodes, to be owned by uid 1000 and gid 100.
  <pre>
  groupadd -g 100 users
  useradd -g 100 -u 1000 jovyan
  mkdir -p /var/tmp/jovyan/data
  chown -R 1000:100 /var/tmp/jovyan/data
  </pre>
  2.  Apply the given yaml manifest to deploy a K8s pod and service for JupyterLab.
  <pre>
  kubectl apply -f https://raw.githubusercontent.com/snpsuen/Deep_Learning_JupyterLab/main/script/jupyter-notebook.yaml
  </pre>
  3.  The lab will run the working directory /home/jovyan that contains the following folders.
  <pre>
  /home/jovyan
  ├── data
  ├── input
  ├── model
  ├── notebook
  ├── work
  </pre>
  All the folders are local to the container, exccept /home/jovyan/data being mounted on /var/tmp/jovyan/data on a K8s node.
  <pre></pre>
  4.  The provided notebook template, https://raw.githubusercontent.com/snpsuen/Deep_Learning_JupyterLab/main/script/Template_of_RNN_TC8_Annually_Local.ipynb, is meant to be executed on Google Colab to build and train an RNN LSTM sample model. The model will subsequenty swing from Colab via this repo to the JuypyterLab container.
