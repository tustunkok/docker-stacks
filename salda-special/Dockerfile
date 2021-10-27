ARG BASE_CONTAINER=tensorflow-notebook
FROM $BASE_CONTAINER

USER $NB_UID

RUN pip install --quiet \
    GPUtil \
    minisom \
    nltk \
    autokeras

RUN pip install --quiet \
    torch==1.7.1+cu110 \
    torchvision==0.8.2+cu110 \
    torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html

RUN conda install --quiet --yes \
    opencv \
    humanize \
    wordcloud \
    pydot \
    && \
    conda install -c conda-forge --quiet --yes \
    xgboost \
    && \
    conda clean --all -f -y && \
    npm cache clean --force && \
    rm -rf /home/$NB_USER/.cache/yarn && \
    rm -rf /home/$NB_USER/.node-gyp && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER

USER $NB_UID
