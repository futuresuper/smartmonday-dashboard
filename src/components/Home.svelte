<script>
  import Slider from "./Slider.svelte";
  import Chart from "./Chart.svelte";
  import data from "../data/dashboard.json";
  import QuestionMark from "./ui/QuestionMark.svelte";

  let age = 16;
  let returnTarget = "";
  let dollarReturn = "";

  function updateAge(n) {
    age = n;
    returnTarget = data[age.toString()].returnTarget;
    dollarReturn = data[age.toString()].return;
  }
</script>

<div class="container">
  <img
    src="/images/sm-logo.png"
    alt="SmartMonday Logo"
    style="width: 245px; margin-bottom: 40px"
  />

  <p style="font-size: 14px; margin-bottom: 40px">
    <a href="https://smartmonday.com.au/Home">Home</a>
    {" > "}
    <a href="https://smartmonday.com.au/Superannuation">Superannuation</a>
    {" > "}
    MySuper Dashboard
  </p>

  <h1>Aon MySuper dashboard</h1>

  <p>Use this dashboard to compare Aon MySuper with other MySuper products.</p>
  <p>
    The dashboard has been calculated for a member having an account balance of
    $50,000.
  </p>
  <p>
    The return and risk information shown below relate to a specific member age
    of the Aon MySuper investment option, selected by moving the age slider left
    or right.
  </p>
  <p>
    Aon MySuper implements a lifecycle investment strategy which automatically
    adjusts to a more defensive investment mix as the member moves through their
    'working week' towards retirement<sup>2</sup>. This is why the return,
    return target and investment risk level generally reduces as the age slider
    is moved to the right. See PDS reference guide
    <a
      href="https://smartmonday.com.au/smartmonday/media/smartmonday/docs/PDS-PRIME-Investment-Options.pdf?ext=.pdf"
      target="_blank">Your investment options</a
    > for more information on Aon MySuper.
  </p>

  <h2>Select your age</h2>

  <Slider {age} {updateAge} />

  <div class="grid">
    <div class="full-width">
      <h3>Statement of fees and other costs<sup>1</sup></h3>
      <div class="left-centre">
        <p class="s">
          <span class="l bold">$517</span>
          per year
        </p>
        <QuestionMark>
          You may be eligible for reduced fees depending on the size of your
          employer's super plan.
        </QuestionMark>
      </div>
    </div>
    <div>
      <div class="left-centre">
        <h3>Return target<sup>2</sup></h3>
        <QuestionMark>
          This MySuper product is intended for members who expect to remain invested until their retirement, and at least a minimum of 5 years.
        </QuestionMark>
      </div>
      <p class="s">
        To provide a return at least {returnTarget}% per year above inflation
        (after fees and taxes) over rolling 10-year periods.
      </p>
      <p class="s">
        The return target is a prediction and therefore can’t be guaranteed.
      </p>
    </div>
    <div>
      <h3>Return<sup>1, 2</sup></h3>
      <p class="l bold">{dollarReturn}% p.a.</p>
      <p class="s">
        This is the average annual return from 1 July 2014 to 30 June 2021.
      </p>
      <p class="s">Aon MySuper commenced on 1 January 2014.</p>
    </div>
    <div>
      <div class="left-centre">
        <h3>Level of investment risk</h3>
        <QuestionMark>
          The Standard Risk Measure (SRM) used here is not a complete assessment of risk. For example, while the SRM indicates the likely frequency of negative annual returns (for a 20-year period), it does not indicate the potential size of negative returns. With respect to the current low interest-rate environment, where market interest rates are relatively low by historical standards, the likely frequency of negative annual returns for interest‑bearing securities may be higher than has traditionally been the case and reflected in the SRM.
        </QuestionMark>
      </div>
      <p class="l bold">Very high</p>
      <p class="s">
        This risk band means we anticipate there will be approximately 6 or more
        years of negative annual returns over any 20-year period.
      </p>
    </div>
    <div class="full-width">
      <h3>Comparison between return target and return<sup>1, 2</sup></h3>
      <div class="graph">
        <Chart {age} />
      </div>
      <p class="disclaimer">
        Past returns are not a reliable indicator of future returns. Please note
        that the average return shown above is a cumulative average since
        inception for each year to 30 June. This measure may differ from other
        dashboards and moving averages for other products. The average return
        for the Aon MySuper product commenced on 1 July 2014, the start of the
        first full financial year after the product was launched. Please take
        this into consideration when using this figure to compare other
        products.The returns shown here do not take into account the member’s
        lifecycle asset allocation adjustments through time. The latest
        performance returns, adjusted for a member’s lifecycle journey, are
        available at <a
          href="https://www.smartmonday.com.au/Documents?cat=investment%20returns"
          target="_blank">smartmonday.com.au</a
        >
      </p>
    </div>
  </div>
  <h2>Footnotes</h2>
  <ol>
    <li class="disclaimer">
      The information shown on this dashboard assumes an account balance of
      $50,000. The standard fees and costs for the product are:
      <ul>
        <li class="disclaimer">asset administration fee 0.44% p.a.</li>
        <li class="disclaimer">member fee $72.00 ($6 per month).</li>
        <li class="disclaimer">investment fee 0.38% p.a.</li>
        <li class="disclaimer">indirect costs of 0.07% p.a.</li>
      </ul>
      Fees and costs may not necessarily be the same in future years.<br/>
      
      You may also be eligible for a reduced asset administration fee depending on
      the size of your employer's super plan. See the PDS reference guide
      <a
        href="https://smartmonday.com.au/smartmonday/media/smartmonday/docs/PDS-PRIME-Fees-and-costs.pdf?ext=.pdf"
        target="_blank"
      >
        Fees and costs
      </a>
      for important information.
    </li>
    <li class="disclaimer">
      Returns shown on this page may differ from returns shown on other parts of
      the smartMonday website, as the returns shown here are reflective of a
      'representative member' (as defined by APRA) and therefore do not take
      into account the member's lifecycle asset allocation adjustments through
      time. The latest performance returns, adjusted for a member's lifecycle
      journey, are available at
      <a
        href="https://smartmonday.com.au/Documents?cat=investment%20returns"
        target="_blank"
      >
        smartmonday.com.au
      </a>
      . The Aon MySuper investment option implements a lifecycle investment strategy
      which automatically adjusts the asset allocation for a member as they move
      through their working life towards retirement. The youngest members are invested
      in approximately 90% growth-style investments (like shares and property) and
      approximately 10% in defensive investments (like cash and bonds). As time progresses
      the investment mix adjusts gradually, and the percentage of growth-style investments
      is reduced, and defensive investments are increased.
    </li>
  </ol>
  <h2>Disclaimer</h2>
  <p class="disclaimer">
    The information contained in this dashboard is general in nature and should
    not be relied upon as personal advice as your personal needs, objectives and
    financial situation have not been considered. Before deciding whether a
    particular product is right for you, please consider the relevant
    <a href="https://smartmonday.com.au/Documents?cat=PDS" target="_blank">
      Product Disclosure Statement
    </a>

    or speak with your financial adviser. If you do not have a financial
    adviser, contact us to ask about the intra-fund advice services you can
    access through your membership. smartMonday is a registered trading name of
    SmartMonday Solutions Limited ABN 48 002 288 646 AFSL 236667 (smartMonday), the
    sponsor of the Aon Master Trust ABN 68 964 712 340 (the Fund). The trustee
    of the Fund is Equity Trustees Superannuation Limited ABN 50 055 641 757
    AFSL 229757 RSE Licence L0001458. This dashboard has been prepared by smartMonday on
    behalf of the trustee. smartMonday PRIME is part of the Fund. smartMonday has taken
    care in the production of this dashboard, the contents of which has been
    obtained from sources that it believes to be reliable. To the extent
    permitted by law, smartMonday and the trustee do not warrant, represent or guarantee
    the accuracy, adequacy, completeness or fitness for any purpose that this
    dashboard may be used and accept no liability for any loss incurred by
    anyone who relies on it. In any case, any recipient shall be entirely
    responsible for their use of this dashboard. Past performance is not a
    reliable indicator of future performance. The Target Market Determinations
    for smartMonday products are available at
    <a href="https://smartmonday.com.au/Governance" target="_blank">
      smartmonday.com.au/governance
    </a>

    . © 2021 SmartMonday Solutions Limited.
  </p>
</div>

<style lang="scss">
  @use "../styles/" as *;

  .container {
    max-width: 1000px;
    margin: 0 auto;
  }

  .grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    > * {
      border: 1px solid $grey;
      padding: 20px;
    }
    .full-width {
      grid-column: span 3;
    }
  }

  .left-centre {
    display: flex;
    flex-direction: row;
    justify-content: left;
    align-items: flex-start;
  }

  ol > li {
    margin-bottom: 20px;
  }

  @media (max-width: 600px) {
    .grid {
      grid-template-columns: 100%;
      > * {
        grid-column: span 1;
      }
      .full-width {
        grid-column: span 1;
      }
    }
  }
</style>
