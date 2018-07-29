FROM jupyter/tensorflow-notebook

USER root

RUN cd .. && \
    wget  https://root.cern.ch/download/cling/cling_2018-07-27_ubuntu17.10.tar.bz2 && \
    tar -xvjf cling_2018-07-27_ubuntu17.10.tar.bz2 && \
    rm cling_*.tar.bz2 && \
    mv cling_* cling

RUN cd .. && \
    ln -s $(pwd)/cling/bin/* /usr/bin/ && \
    cd cling/share/cling/Jupyter/kernel && \
    pip install -e . && \
    jupyter-kernelspec install cling-cpp17 && \
    jupyter-kernelspec install cling-cpp14 && \
    jupyter-kernelspec install cling-cpp11

RUN chown -R $NB_USER /home/$NB_USER && \
    rm -rf /home/$NB_USER/.local/share/jupyter


# Reset user from jupyter/base-notebook
USER $NB_USER

