# C= SN (d_)- Ke"™N (d,) 

def price monte_carlo call(ticker, K=None, t=1.0, r=0.05, n_sims=100, n_steps=252): 

stock data = yf.download(ticker, period="2y", progress=False) stock_da‘Log Re **t** urns’a[ ] = np.log(stock_data[‘Close’] / stock _data[ ‘Close’ ].shift(1)) stock _data = stock _data.dropna() P_@ = stock _data[ ‘Close’ ].iloc[-1] daily volatility = stock _data[ "LogReturns’].std() sigma = daily volatility * np.sqrt(252) 

dt = t/n_steps 

S = np.zeros((n_ steps + 1, n_sims)) s[e] = Pe for t_step in range(1, n_steps + 1): Z = np.random.standardnormal(n sims) drift = (r-@.5*sigma**2)*dt shock = sigma * np.sgqrt(dt) * z 

§[t_step] = S[t_step-1] * np.exp(drift + shock) 

final_prices = S[-1] 

if K is None: K = P6.item() 

P, = Py, -e!r—sal **o** ~|\At+ov_2)At+ AtZ 

payoffs = np.maximum(Tinal prices - K, @) expected payotf = np.mean(payofts) discount_factor = np.exp(-r*t) monte_ **c** allarloprice = expected payoff * discount_factor 

return{ 

"Ticker": ticker, 

“Call Price": round(floc **a** rlot(montecall price), 2), “Strike Price": round(K, 2) 1 J 

> P, = P;-1-e"-27)r—so")dt+avdtZ1 2 - Swing: 

swing occurs = np.random.rand(nsims) < freq swing multiplier = np.ones(n sims) 

num swings = np.sum(swing occurs) if num swings > @: directions = rng.choice([-1,1], size=num_ swings) swingmultiplier[swingoccurs] = 1 + delta * directions 

S[t_step] = S[t_step-1] * np.exp(drift + shock) * swing multiplier 



<!-- Start of picture text -->
Monte Carlo Simulation: AAPL Price Paths (1 year)<br>400 VW sCBlack Swan Event Vv<br>--- Starting Price: $273.58 A<br>350 fy . a<br>vy}<br>& 300 | v |<br>in a RON Ulan poate hee drtdel ie mangos Pen selon dh omeaapenbanhowe<br>250 NyV\' \ AY 3 } ¥<br>3<br>pr rnnfyrr v<br>Tl | v<br>200<br>0 50 100 150 200 250<br>Trading Days<br><!-- End of picture text -->

def extract_data(data,ticker,t): 

close data = data["Close"] 

if isinstance(closedata, pd.DataFrame): prices = close data[ticker | else: prices = close data log returns = np.log(prices / prices.shift(1)).dropna() day_std = logreturns.std() 

o = float(day std) * np.sqrt(252) § = float(prices.iloc[-1]) return 5,0 

def make_d1 d2(S,K,r,o,t): d1 = (math.log(S/K) + (r + (0**2)/2) * t)/(o * math.sqrt(t)) d2 = di - o * math.sqrt(t) return di, d2 

det black scholescall(S,K,r,t,d1,d2): Ndi = norm.cdf(d1) Nd2 = norm.cdf(d2) C = S * Ndi - K * np.exp(-r * t) * Nd? return C 

# C= SN (d,)- Ke"™N (d,) 

def blackscholes(ticker,K,t,r,call_ put,start,end): data = yf.download(ticker, start=start, end=end, autoadjust=True) 5,0 = extract data(data,ticker,t) di,d2 = make did2(S,K,r,o,t) if call put == “call”: option price = black scholescall(S,K,r,t,d1,d2) elif call put == “put”: option_price = black_scholes_put(S,K,r,t,d1,d2) else: return "Must enter call or put" return f"{ticker}: {call put} option price is {option price}" 

