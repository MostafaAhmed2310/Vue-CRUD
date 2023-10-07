<template>
    <div class="modal fade" id="viewInvoice" tabindex="-1" aria-labelledby="viewInvoiceModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="container">
                    <div class="row">
                        <div class="col-sm-12 flex">
                        <div class="col-sm-6">
                            <div class="bold_text title">
                            فاتورة ضريبية
                            </div>
                            <div class="row center">
                            <div class="col-sm-6">
                                <div>التاريخ</div>
                                <span>12/10/2023</span>
                            </div>
                            <div class="col-sm-6">
                                <div>الرقم التسلسلي</div>
                                <span>1234567</span>
                            </div>
                            </div>
                        </div>
                        <div class="col-sm-6 text-end">
                            <img src="@/assets/QR_code.svg" alt="QR Code">
                        </div>
                        </div>
                    </div>
                    
                    <div class="row">
                        <div class="col-sm-12">
                        <div class="text-right bold_text">معلومات البائع</div>
                        <div class="row">
                            
                            <div class="col-sm-9 right_container">
                            <div class="row">
                                <div class="col-sm-4 vertical-line">
                                <div>سن البائع</div>
                                <span>1234567</span>
                                </div>
                                <div class="col-sm-4 vertical-line">
                                <div>عنوان البائع</div>
                                <span>1234567</span>
                                </div>
                                <div class="col-sm-4">
                                <div>رقم تسجيل ضريبة القيمة المضافة للبائع</div>
                                <span>1234567</span>
                                </div>
                            </div>
                            </div>
                            <div class="col-sm-3">
                            <div>
                                <div>رقم السجل التجاري</div>
                                <span>1234567</span>
                            </div>
                            </div>
                        </div>
                        </div>
                    </div>
                    
                    <div class="row">
                        <div class="col-sm-12">
                        <div class="text-right bold_text">معلومات المشتري</div>
                        <div class="row">
                            <div class="col-sm-3 vertical-line">
                            <div class="title_div">
                                <div>سن المشتري</div>
                                <span>1234567</span>
                            </div>
                            </div>
                            <div class="col-sm-3 vertical-line">
                            <div class="title_div">
                                <div>عنوان المشتري</div>
                                <span>1234567</span>
                            </div>
                            </div>
                            <div class="col-sm-3">
                            <div class="title_div">
                                <div>رقم السجل التجاري</div>
                                <span>1234567</span>
                            </div>
                            </div>
                            <div class="col-sm-3">
                            <div class="title_div">
                                <div>رقم تسجيل ضريبة القيمة المضافة للمشتري</div>
                                <span>1234567</span>
                            </div>
                            </div>
                        </div>
                        </div>
                    </div>
                    
                    <div class="container-table">
                        <div class="row">
                        <div class="col-12">
                            <table class="table">
                            <thead class="thead-dark">
                                <tr class="col-12">
                                <th class="col-1">المنتج</th>
                                <th class="col-2">سعر الوحدة</th>
                                <th class="col-1">الكمية</th>
                                <th class="col-2">المجموع الفرعي بدون ضريبة</th>
                                <th class="col-1">نسبة الضريبة</th>
                                <th class="col-1">قيمة الضريبة</th>
                                <th class="col-4">المجموع شامل ضريبة القيمة المضافة</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                <td class="col-1">منتج 1</td>
                                <td class="col-2">60</td>
                                <td class="col-1">3</td>
                                <td class="col-2">180</td>
                                <td class="col-1">15%</td>
                                <td class="col-1">27</td>
                                <td class="col-4">207</td>
                                </tr>
                                <tr>
                                <td class="col-1">منتج 2</td>
                                <td class="col-2">40</td>
                                <td class="col-1">2</td>
                                <td class="col-2">80</td>
                                <td class="col-1">15%</td>
                                <td class="col-1">12</td>
                                <td class="col-4">92</td>
                                </tr>
                            </tbody>
                            </table>
                        </div>
                        </div>
                    </div>
                    
                    <div class="row">
                        <div class="col-sm-12">
                        <span class="bold_text title_div">المجموع</span>
                        <span class="left_text">260</span>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-sm-12">
                        <span class="bold_text title_div">ضريبة القيمة المضافة (15%)</span>
                        <span class="left_text">39</span>
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-sm-12">
                        <span class="bold_text title_div">المجموع مع الضريبة (15%)</span>
                        <span class="left_text">299</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'InvoiceModal',
    props: {
        
    },
    data(){
        return{
            
        }
    },
    methods:{},
    mounted(){},
    updated(){
       
    }
}
</script>

<style scoped>
.container {
        direction: rtl;
        background-color: rgb(226, 236, 217);
        padding: 20px 40px;
    }
    .right_container {
        text-align: right;
    }
    .title {
        font-size: xx-large;
        font-weight: 800;
        text-align: center;
        margin-bottom: 10px;
    }
    .center{
        text-align: center;
        margin-bottom: 10px;
    }
    .title_div {
        text-align: right;
    }
    .bold_text {
        font-weight: 700;
    }
    img {
        width: 50%;
        text-align: right;
    }
    .container-table{
        text-align: center;
        background: rgb(226, 236, 217);
    }
    .container-table .col-1,
    .container-table .col-2,
    .container-table .col-4{
        background: rgb(226, 236, 217);
    }
    .vertical-line {
        border-left: 1px solid black;
        height: 100%;
    }
    .left_text{
        float: left;
    }
    .flex{
        display: flex;
    }
    .text-end{
        text-align: end !important;
    }
</style>
