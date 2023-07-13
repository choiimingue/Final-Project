# Final-Project

![banner_01](https://github.com/choiimingue/Final-Project/assets/122662827/31aad895-5b67-4a86-b2d6-e723f286ae47)

본 프로젝트는 개인 OpenAI API Key를 활용하여 제작되었습니다. 
과금 문제 및 개인 정보 보안 문제로 인해 최종 결과물의 시연 영상을 함께 첨부해 놓았음을 미리 밝힙니다. 
로컬에서 구동하기 위해서는 아래와 같은 추가적인 과정이 요구됩니다.
1. Python의 `dotenv` 라이브러리 install
2. `.env` 파일을 `05_streamlit` 디렉토리에 생성
3. OpenAI에서 발급받은 API Key를 `OPENAI_API_KEY = 발급받은 Key` 와 같이 입력하고 저장

보다 자세한 과정은 [link](https://blog.gilbok.com/how-to-use-dot-env-in-python/)를 참고하세요.

단, 본 프로젝트 파일을 구동함으로써 발생하는 API Key 사용 과금 비용은 작성자가 부담하지 않으며 활용하는 주체들이 부담해야함을 알려드립니다.

# Cook Chat! : 남은 식재료와 원하는 테마를 입력하면 레시피를 추천해주는 챗봇
![concept 1](https://github.com/choiimingue/Final-Project/assets/122662827/ae27e36c-1a30-4b7e-839c-2a1dc6574358)

### 기능 소개
- **레시피 추천** : 보유한 식재료 및 테마를 챗봇에게 전달하면 이를 기반으로 레시피를 추천합니다.
- **레시피 설명** : 레시피에 대한 설명이 필요하다면 "레시피에 대해 설명해줘."와 같이 요구해보세요. 
- **레시피 재료** : 추천된 레시피에 필요한 재료는 무엇인지 알려줍니다.
- **재추천** : 재추천을 요구할 수도 있습니다. (***다만, 재추천은 일정한 성능을 보장하지 않습니다.***)
- **식재료 구매 링크** : 부족한 재료가 있다면 재료를 클릭해보세요. 24시간 이내 배송되는 사이트로 연결해줍니다.

### 기대 효과

***구매자에게는 필요한 소비를 판매자에게는 고객 타켓팅을***

- 사용자는 남는 재료 처리, 요리법 서치 등 생활의 번거로움을 챗봇과의 간결하고 유연한 인터랙션으로 해소할 수 있습니다.
- 공급자는 부족한 재료를 구매할 수 있도록 노출된 링크를 통해 유입되는 사용자들을 확보함으로써 고객 타겟팅 노출 광고와 유사한 효과를 볼 수 있을 것으로 기대합니다.
- 챗봇 UI를 통한 추천시스템으로 콜드 스타트 상황에서도 다소 한정된 범위 내에서 이긴 하지만 유연하고 즉각적인 추천이 가능하며 유저와의 상호작용에서 얻은 데이터를 지속적으로 학습시킴으로써 성능을 더 고도화시킬 수도 있을 것입니다.

## 활용 기술
![overview](https://github.com/choiimingue/Final-Project/assets/122662827/3da147fb-29b7-43b1-bcf8-dfe42ca2aed6)


For a visual introduction to NeuralProphet, [view this presentation](notes/NeuralProphet_Introduction.pdf).

## Contribute
We compiled a [Contributing to NeuralProphet](CONTRIBUTING.md) page with practical instructions and further resources to help you become part of the family. 

## Community
#### Discussion and Help
If you have any question or suggestion, you can participate with [our community right here on Github](https://github.com/ourownstory/neural_prophet/discussions)

#### Slack Chat
We also have an active [Slack community](https://join.slack.com/t/neuralprophet/shared_invite/zt-sgme2rw3-3dCH3YJ_wgg01IXHoYaeCg). Come and join the conversation!

## Tutorials
[![Open All Collab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ourownstory/neural_prophet)

There are several [example notebooks](docs/source/tutorials) to help you get started. 

You can find the datasets used in the tutorials, including data preprocessing examples, in our [neuralprophet-data repository](https://github.com/ourownstory/neuralprophet-data).

Please refer to our [documentation page](https://neuralprophet.com) for more resources.

### Minimal example
```python
from neuralprophet import NeuralProphet
```
After importing the package, you can use NeuralProphet in your code:
```python
m = NeuralProphet()
metrics = m.fit(df)
forecast = m.predict(df)
```
You can visualize your results with the inbuilt plotting functions:
```python
fig_forecast = m.plot(forecast)
fig_components = m.plot_components(forecast)
fig_model = m.plot_parameters()
```
If you want to forecast into the unknown future, extend the dataframe before predicting:
```python
m = NeuralProphet().fit(df, freq="D")
df_future = m.make_future_dataframe(df, periods=30)
forecast = m.predict(df_future)
fig_forecast = m.plot(forecast)
```
## Install
You can now install neuralprophet directly with pip:
```shell
pip install neuralprophet
```

### Install options

If you plan to use the package in a Jupyter notebook, we recommended to install the 'live' version:
```shell
pip install neuralprophet[live]
```
This will allow you to enable `plot_live_loss` in the `fit` function to get a live plot of train (and validation) loss.

If you would like the most up to date version, you can instead install direclty from github:
```shell
git clone <copied link from github>
cd neural_prophet
pip install .
```

## Features
### Model components
* Autoregression: Autocorrelation modelling - linear or NN (AR-Net)
* Trend: Piecewise linear trend with optional automatic changepoint detection
* Seasonality: Fourier terms at different periods such as yearly, daily, weekly, hourly.
* Lagged regressors: Lagged observations (e.g temperature sensor) - linear or NN
* Future regressors: In advance known features (e.g. temperature forecast) - linear
* Events: Country holidays & recurring custom events


### Framework features
* Multiple time series: Fit a global/glocal model with (partially) shared model parameters
* Uncertainty: Estimate values of specific quantiles - Quantile Regression
* Regularize modelling components
* Plotting of forecast components, model coefficients and more
* Time series crossvalidation utility
* Model checkpointing and validation


### Coming soon<sup>:tm:</sup>

* Cross-relation of lagged regressors
* Cross-relation and non-linear modelling of future regressors
* Static features / Time series featurization
* Logistic growth for trend component.
* Model bias modelling / correction with secondary model
* Multimodal seasonality

For a list of past changes, please refer to the [releases page](https://github.com/ourownstory/neural_prophet/releases).

The vision for future development can be seen at [Development Timeline](notes/development_timeline.md) (partially outdated).

## Cite
Please cite [NeuralProphet](https://arxiv.org/abs/2111.15397) in your publications if it helps your research:
```
@misc{triebe2021neuralprophet,
      title={NeuralProphet: Explainable Forecasting at Scale}, 
      author={Oskar Triebe and Hansika Hewamalage and Polina Pilyugina and Nikolay Laptev and Christoph Bergmeir and Ram Rajagopal},
      year={2021},
      eprint={2111.15397},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```

## About
NeuralProphet is and open-source community project, supported by awesome people like you. 
If you are interested in joining the project, please feel free to reach out to me (Oskar) - you can find my email on the [NeuralProphet Paper](https://arxiv.org/abs/2111.15397).
