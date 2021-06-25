FROM conda/miniconda3-centos7:latest

RUN yum -y update \
     && yum -y install libarchive-devel \
     && yum clean all

# XRootD + CA + VOMS + Coffea
RUN conda install --yes --freeze-installed \
      -c conda-forge \
      conda-build \
      voms \
      jupyterlab \
      dask_labextension \
      python==3.8.* \
      ca-policy-lcg \
      xrootd \
      "uproot>=4.0.8" \
      coffea==0.7.4 \
      lz4 python-xxhash zstandard \
      && conda clean --all -f -y \
      && conda build purge-all

# Make a symbolic link between installation /opt/conda/etc/grid-security and actual directory /etc/grid-security
RUN ln -s /opt/conda/etc/grid-security /etc/grid-security
