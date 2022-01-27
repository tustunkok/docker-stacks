ARG BASE_CONTAINER=tensorflow-notebook
FROM $BASE_CONTAINER

USER $NB_UID

RUN pip install --quiet \
    GPUtil \
    minisom \
    nltk \
    autokeras

RUN mamba install --quiet --yes \
    opencv \
    humanize \
    wordcloud \
    pydot \
    && \
    conda install -c conda-forge --quiet --yes \
    xgboost \
    && \
    mamba clean --all -f -y && \
    npm cache clean --force && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

USER $NB_UID
