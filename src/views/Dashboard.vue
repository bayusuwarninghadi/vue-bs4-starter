<template>
    <div>
        <base-header class="pb-6 pb-8 pt-5 pt-md-8 bg-gradient-success">
            <!-- Card stats -->
        </base-header>

        <!--Charts-->
        <b-container class="mt--7">
            <b-row>
                <b-col xl="8" class="mb-4 mb-xl-0">
                    <b-row>
                        <b-col xl="8" class="mb-6 mb-xl-0">
                            <h1>
                                Video
                                <small class="float-right mt-2">Browse all video</small>
                            </h1>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col xl="8" class="mb-6 mb-xl-0">
                            <div class="mb-4">
                                <card type="default" header-classes="bg-transparent">
                                    <b-row align-v="center" slot="header">
                                        <b-col>
                                            <h6 class="text-light text-uppercase ls-1 mb-1">Overview</h6>
                                            <h5 class="h3 text-white mb-0">Sales value</h5>
                                        </b-col>
                                        <b-col>
                                            <b-nav class="nav-pills justify-content-end">
                                                <b-nav-item
                                                        class="mr-2 mr-md-0"
                                                        :active="bigLineChart.activeIndex === 0"
                                                        link-classes="py-2 px-3"
                                                        @click.prevent="initBigChart(0)">
                                                    <span class="d-none d-md-block">Month</span>
                                                    <span class="d-md-none">M</span>
                                                </b-nav-item>
                                                <b-nav-item
                                                        link-classes="py-2 px-3"
                                                        :active="bigLineChart.activeIndex === 1"
                                                        @click.prevent="initBigChart(1)"
                                                >
                                                    <span class="d-none d-md-block">Week</span>
                                                    <span class="d-md-none">W</span>
                                                </b-nav-item>
                                            </b-nav>
                                        </b-col>
                                    </b-row>
                                    <line-chart
                                            :height="335"
                                            ref="bigChart"
                                            :chart-data="bigLineChart.chartData"
                                            :extra-options="bigLineChart.extraOptions"
                                    >
                                    </line-chart>
                                </card>
                            </div>
                        </b-col>
                        <b-col xl="4" class="mb-6 mb-xl-0">
                            <img src="https://picsum.photos/id/231/300/300" class="img-thumbnail img-responsive mb-4" >
                            <img src="https://picsum.photos/id/230/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/235/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/238/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/237/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                    </b-row>
                </b-col>

                <b-col xl="4" class="mb-4 mb-xl-0">
                    <b-row>
                        <b-col xl="12">
                            <h1>
                                Activity
                                <small class="float-right mt-2">View Timeline</small>
                            </h1>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col v-for="item in pills" xs="12" lg="12">
                            <div class="card card-stats mb-4">
                                <div class="card-body">
                                    <div class="row">
                                        <div class="col">
                                            <h5 class="card-title text-uppercase text-muted mb-0">{{item.title}}</h5>
                                            <span class="h2 font-weight-bold mb-0">{{item.value}}</span>
                                        </div>
                                    </div>
                                    <p class="mt-3 mb-0 text-sm"><span class="text-success mr-2">{{item.percentage}}</span>
                                        <span class="text-nowrap">{{item.subtitle}}</span>
                                    </p>
                                </div>
                            </div>
                        </b-col>
                    </b-row>
                </b-col>
            </b-row>
            <!-- End charts-->

            <br>
            <b-row>
                <b-col xl="8" class="mb-4 mb-xl-0">
                    <b-row>
                        <b-col xl="8" class="mb-6 mb-xl-0">
                            <h1>
                                Video
                                <small class="float-right mt-2">Browse all video</small>
                            </h1>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col xl="8" class="mb-6 mb-xl-0">
                            <div class="mb-4">
                                <card header-classes="bg-transparent">
                                    <b-row align-v="center" slot="header">
                                        <b-col>
                                            <h6 class="text-uppercase text-muted ls-1 mb-1">Performance</h6>
                                            <h5 class="h3 mb-0">Total orders</h5>
                                        </b-col>
                                    </b-row>

                                    <bar-chart
                                            :height="335"
                                            ref="barChart"
                                            :chart-data="redBarChart.chartData"
                                    >
                                    </bar-chart>
                                </card>
                            </div>
                        </b-col>
                        <b-col xl="4" class="mb-6 mb-xl-0">
                            <img src="https://picsum.photos/id/231/300/300" class="img-thumbnail img-responsive mb-4" >
                            <img src="https://picsum.photos/id/230/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/235/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/238/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                        <b-col xl="4" class="mb-xl-0">
                            <img src="https://picsum.photos/id/237/300/300" class="img-thumbnail img-responsive mb-4" >
                        </b-col>
                    </b-row>
                </b-col>

                <b-col xl="4" class="mb-4 mb-xl-0">
                    <b-row>
                        <b-col xl="12">
                            <h1>
                                Activity
                                <small class="float-right mt-2">View Timeline</small>
                            </h1>
                        </b-col>
                    </b-row>
                    <b-row>
                        <b-col v-for="item in pills" xs="12" lg="12">
                            <div class="card card-stats mb-4">
                                <div class="card-body">
                                    <div class="row">
                                        <div class="col">
                                            <h5 class="card-title text-uppercase text-muted mb-0">{{item.title}}</h5>
                                            <span class="h2 font-weight-bold mb-0">{{item.value}}</span>
                                        </div>
                                    </div>
                                    <p class="mt-3 mb-0 text-sm"><span class="text-success mr-2">{{item.percentage}}</span>
                                        <span class="text-nowrap">{{item.subtitle}}</span>
                                    </p>
                                </div>
                            </div>
                        </b-col>
                    </b-row>
                </b-col>
            </b-row>
            <!-- End charts-->

            <!--Tables-->
            <b-row class="mt-5">
                <b-col xl="8" class="mb-4 mb-xl-0">
                    <page-visits-table></page-visits-table>
                </b-col>
                <b-col xl="4" class="mb-4 mb-xl-0">
                    <social-traffic-table></social-traffic-table>
                </b-col>
            </b-row>
            <!--End tables-->
        </b-container>

    </div>
</template>
<script>
    // Charts
    import * as chartConfigs from '@/components/Charts/config';
    import LineChart from '@/components/Charts/LineChart';
    import BarChart from '@/components/Charts/BarChart';

    // Components
    import BaseProgress from '@/components/BaseProgress';
    import StatsCard from '@/components/Cards/StatsCard';

    // Tables
    import SocialTrafficTable from './Dashboard/SocialTrafficTable';
    import PageVisitsTable from './Dashboard/PageVisitsTable';

    export default {
        components: {
            LineChart,
            BarChart,
            BaseProgress,
            StatsCard,
            PageVisitsTable,
            SocialTrafficTable
        },
        data() {
            return {
                pills: [
                    {title: 'Foo 1', value: '150', percentage: '20%', subtitle: 'lipsum 1'},
                    {title: 'Foo 2', value: '150', percentage: '30%', subtitle: 'lipsum 2'},
                    {title: 'Foo 3', value: '150', percentage: '50%', subtitle: 'lipsum 3'},
                    {title: 'Foo 4', value: '150', percentage: '88%', subtitle: 'lipsum 4'},
                    {title: 'Foo 1', value: '150', percentage: '20%', subtitle: 'lipsum 5'}
                ],
                bigLineChart: {
                    allData: [
                        [0, 20, 10, 30, 15, 40, 20, 60, 60],
                        [0, 20, 5, 25, 10, 30, 15, 40, 40]
                    ],
                    activeIndex: 0,
                    chartData: {
                        datasets: [
                            {
                                label: 'Performance',
                                data: [0, 20, 10, 30, 15, 40, 20, 60, 60],
                            }
                        ],
                        labels: ['May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    },
                    extraOptions: chartConfigs.blueChartOptions,
                },

                redBarChart: {
                    chartData: {
                        labels: ['Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                        datasets: [{
                            label: 'Sales',
                            data: [25, 20, 30, 22, 17, 29]
                        }]
                    },
                    extraOptions: chartConfigs.blueChartOptions
                }
            };

        },
        methods: {
            initBigChart(index) {
                let chartData = {
                    datasets: [
                        {
                            label: 'Performance',
                            data: this.bigLineChart.allData[index]
                        }
                    ],
                    labels: ['May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                };
                this.bigLineChart.chartData = chartData;
                this.bigLineChart.activeIndex = index;
            }
        },
        mounted() {
            this.initBigChart(0);
        }
    };
</script>
<style>
    .el-table .cell {
        padding-left: 0px;
        padding-right: 0px;
    }
</style>
