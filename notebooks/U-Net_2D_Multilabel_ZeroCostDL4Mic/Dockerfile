FROM tensorflow/tensorflow:2.8.0-gpu
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

ARG NOTEBOOK_NAME=U-Net_2D_Multilabel_ZeroCostDL4Mic.ipynb

RUN pip install jupyterlab

WORKDIR /home
COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY ./${NOTEBOOK_NAME} .

RUN git clone https://github.com/IvanHCenalmor/colab_to_docker.git
RUN python3 colab_to_docker/src/transform.py -p ./ -n ${NOTEBOOK_NAME}
RUN rm ${NOTEBOOK_NAME}
RUN mv colabless_${NOTEBOOK_NAME} ${NOTEBOOK_NAME}

CMD [ "jupyter-lab", "${NOTEBOOK_NAME}", "--ip='0.0.0.0'", "--port=8888", "--no-browser", "--allow-root" ]
