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
 
