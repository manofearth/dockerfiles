# Example of launch-function:
#
#function jupyter {
#  if [[  "$(docker ps -q -f name=jupyter)" ]]; then
#    echo "jupyter is running"
#  elif [[ "$(docker ps -a -q -f name=jupyter)" ]]; then
#    echo "starting jupyter"
#    docker container start jupyter
#    sleep 5
#  else
#    echo "creating jupyter"
#    nohup docker run \
#      -v $HOME/Documents/jupyter:/home/jupyter/notebooks \
#      -p 8888:8888 \
#      --name jupyter \
#      manofearth/jupyter &
#    sleep 5
#  fi
#  google-chrome http://localhost:8888
#}

FROM continuumio/anaconda:latest

#  Jupyter update
RUN conda install jupyter -y

RUN useradd --create-home jupyter
USER jupyter

# jupyter-vim-binding extension
RUN mkdir -p $(jupyter --data-dir)/nbextensions \
    && git clone --depth=1 https://github.com/lambdalisue/jupyter-vim-binding $(jupyter --data-dir)/nbextensions/vim_binding \
    && jupyter nbextension enable vim_binding/vim_binding

ENTRYPOINT ["/opt/conda/bin/jupyter"]
CMD ["notebook", "--notebook-dir=/home/jupyter/notebooks", "--ip='*'", "--port=8888", "--no-browser"]
